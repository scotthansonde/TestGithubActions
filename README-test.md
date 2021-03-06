# electricDrummerDev

<a href="https://github.com/scotthansonde">Scott Hanson</a> has built a test package of <a href="http://docserver.scripting.com/drummer/electricDrummer.opml">Electric Drummer</a> than runs on Linux (tested on Ubutu 20.04.2)

- Download the package from https://s3.amazonaws.com/publicfolder.papascott.de/electricdrummer_0.4.4_amd64.deb 

- In the terminal `sudo apt install ./electricdrummer_0.4.4_amd64.deb`

- In the terminal run `electricDrummer`

## Steps to build a deb package for Electric Drummer <br /> (tested on Mac and Linux server)

- On a Mac, the <a href="https://github.com/electron-userland/electron-installer-debian#requirements">deb packager</a> needs two command line tools: dpkg and fakeroot

  - The easiest way to install these is with <a href="https://brew.sh/">homebrew</a>

  - When homebrew is installed, then `brew install fakeroot dpkg` 

  - On Ubtuntu Linux (server or desktop) these commands should already be installed

- git clone the electric drummer repository

- Add a description field to package.json, the deb packager needs it

- `npx electron-packager . "electricDrummer" --platform=linux --arch=x64 --overwrite --icon=drummer.icns --electron-version=7.1.10`

  - npx lets us run npm packages without installing them

  - Set the appname to match "name" in package.json, the deb packager seems to be fussy about the name

  - Only build x64 arch to save time

- `npx electron-installer-debian --src electricDrummer-linux-x64 --dest Packages --arch amd64`

  - Set --dest to whereever the deb package should be saved

