The iceman fork
===============
[![Build Status](https://travis-ci.org/iceman1001/proxmark3.svg?branch=master)](https://travis-ci.org/iceman1001/proxmark3)  [![Coverity Status](https://scan.coverity.com/projects/5117/badge.svg)](https://scan.coverity.com/projects/proxmark3_iceman_fork)  [![Latest release] (https://img.shields.io/github/release/iceman1001/proxmark3.svg)](https://github.com/iceman1001/proxmark3/releases/latest)

##This fork is HIGHLY experimental (or bleeding edge)

##Donate
https://paypal.me/iceman1001/
Feel free to donate. All support is welcome.

##Notice      
There is so much in this fork,  with all fixes and additions its basically the most enhanced fork to this day for the Proxmark3 device. Which makes it so awesum to play with. Do please play with it. Get excited and experiment. As a side note with all coverity scan fixes this client is much more stable than PM3 Master even if I tend to break it sometimes. I'll try to make a release when this fork becomes stable between my experiments.

##Official
The official Proxmark repository is found here: https://github.com/Proxmark/proxmark3

##Coverity Scan Config & Run
Download the Coverity Scan Self-buld and install it.
You will need to configure  ARM-NON-EABI- Compiler for it to use:

- Configure
`cov-configure --comptype gcc --compiler  /opt/devkitpro/devkitARM/bin/arm-none-eabi-gcc`

- run it (I'm running on Ubuntu)
`cov-build --dir cov-int make all`

- make a tarball
`tar czvf proxmark3.tgz cov-int`

- upload it to coverity.com

##Whats changed?
Whats so special with this fork?  I have scraped the web for different enhancements to the PM3 source code and not all of them ever found their way to the master branch. 
Among the stuff is

	* Jonor's hf 14a raw timing patch
	* Piwi's updates. (usually gets into the master)
	* Piwi's "topaz" branch
	* Piwi's "hardnested" branch 
	* Holiman's iclass, (usually gets into the master)
	* Marshmellow's fixes (usually gets into the master)
	* Midnitesnake's Ultralight,  Ultralight-c enhancements
	* Izsh's lf peak modification / iir-filtering
	* Aspers's tips and tricks from inside the PM3-gui-tool, settings.xml and other stuff.
	* My own desfire, Ultralight extras, LF T55xx enhancements, bugs fixes (filelength, hf mf commands ), TNP3xxx lua scripts,  Awid26,  skidata scripts (will come)
	* other obscure patches like for the sammy-mode,  (offline you know), tagidentifications, defaultkeys. 
	* Minor textual changes here and there.
	* Simulation of Ultralight/Ntag.
	* Marshmellow's and my "RevEng" addon for the client.  Ref: http://reveng.sourceforge.net/    Now using reveng1.44
	* J-Run alternative bruteforce Mifare nested auths.. (you need one other exe to make it work)
	* A Bruteforce for T55XX passwords against tag.
	* A Bruteforce for AWID 26, starting w a facilitycode then trying all 0xFFFF cardnumbers via simulation. To be used against a AWID Reader.
	* A Bruteforce for HID,  starting w a facilitycode then trying all 0xFFFF cardnumbers via simulation. To be used against a HID Reader.
	* Blaposts Crapto1 v3.3
    * Icsom's  legic script and legic enhancements
    * Aczid's bitsliced bruteforce solver in 'hf mf hardnested'
	
---	
##Why don't you merged with offical PM3 Master?
I don't actually know how to make small pull-request to github :( and that is the number one reason for me not pushing a lot of things back to the PM3 master.
Me fiddling with the code so much, there is a nightmare in merging a PR.  Luckily I have @marshmellow42 who takes some stuff and push PR's back.

##Why don't you add nnnn or mmmm functionality?
Give me a hint, and I'll see if I can't merge in the stuff you have. 
	
##PM3 GUI
I do tend to rename and move stuff around, the official PM3-GUI from Gaucho will not work so well. *sorry*	

##Development
This fork now compiles just fine on 
   - Windows/mingw environment with Qt5.6.1 & GCC 4.8
   - Ubuntu 1404, 1510, 1604
   - Mac OS X / Homebrew
   - Docker container

##Setup and build for UBUNTU
GC made updates to allow this to build easily on Ubuntu 14.04.2 LTS, 15.10 or 16.04
See https://github.com/Proxmark/proxmark3/wiki/Ubuntu%20Linux

A nice and cool install script made by @daveio is found here: 
https://github.com/daveio/attacksurface/blob/master/proxmark3/pm3-setup.sh

- Run		
`sudo apt-get install p7zip git build-essential libreadline5 libreadline-dev libusb-0.1-4 libusb-dev libqt4-dev perl pkg-config wget libncurses5-dev gcc-arm-none-eabi`

- Clone iceman fork		
`git clone https://github.com/iceman1001/proxmark3.git`

- Get the latest commits	
`git pull`

- Install the blacklist rules	
`make udev`

- add user to dialout group (if you on a Linux/ubuntu/debian). If you do this one, you need to logout and login in again to make sure your rights got changed.	
`sudo adduser $USER dialout`

- Clean and complete compilation	
`make clean && make all`
	
- Flash the BOOTROM		
`client/flasher /dev/ttyACM0 -b bootrom/obj/bootrom.elf`

- Flash the FULLIMAGE	
`client/flasher /dev/ttyACM0 armsrc/obj/fullimage.elf`
	
- Change into the client folder		
`cd client`
	
- Run the client	
`./proxmark3 /dev/ttyACM0`
						   
##Homebrew (Mac OS X)
These instructions comes from @Chrisfu, where I got the proxmark3.rb scriptfile from.
Further questions about Mac & Homebrew,  contact @Chrisfu  (https://github.com/chrisfu/)

1. Install homebrew if you haven't yet already done so: http://brew.sh/

2. Tap this repo: `brew tap iceman1001/proxmark3`

3. Install Proxmark3: `brew install proxmark3` for stable release or `brew install --HEAD proxmark3` for latest non-stable from GitHub.

##Docker container
I recently added a docker container on Docker HUB.  You find it here: https://hub.docker.com/r/iceman1001/proxmark3/
Follow those instructions to get it up and running.  No need for the old proxspace-environment anymore.

[1.6.0] How to start:   https://www.youtube.com/watch?v=b5Zta89Cf6Q
[1.6.0] How to connect: https://youtu.be/0ZS2t5C-caI
[1.6.1] How to flash:   https://www.youtube.com/watch?v=WXouhuGYEiw

Recommendations:  Use only latest container.


## Building on Windows
### 1. QT Open Source
Download QT 5.6.1: http://download.qt.io/archive/qt/5.6/5.6.1-1/qt-opensource-windows-x86-mingw492-5.6.1-1.exe		
Install to `C:\Qt` and choose the following components to be installed:		
- QT - MinGW 32 bit
- Tools - MinGW

In your shell from MSYS (see below), make sure you set QTDIR to your QT installation and add its bin to your path as well:		
`export QTDIR=/c/Qt/5.6/mingw49_32`		
`export PATH=$PATH:$QTDIR/bin`

### 2. MSYS
MSYS is a collection of GNU utilities such as bash, make, gawk and grep to allow building of applications and programs which depend on traditionally UNIX tools to be present. It is intended to supplement MinGW and the deficiencies of the cmd shell.

Download MSYS: http://downloads.sourceforge.net/mingw/MSYS-1.0.11.exe

Follow the installation procedure, you may want to install MSYS to `C:\Qt\msys` and when asked where is your MinGW installation and for its path answer the following: `c:/Qt/Tools/mingw492_32`

### 3. Readline
Download and unpack: https://sourceforge.net/projects/gnuwin32/files/readline/5.0-1/readline-5.0-1-bin.zip/download		

`bin/*` to `C:\Qt\5.6\Tools\mingw492_32\bin`		
`include/*` to `C:\Qt\5.6\Tools\mingw492_32\include`		
`lib/*` to `C:\Qt\5.6\Tools\mingw492_32\lib`

### 4. LibUSB
Download and unpack: https://sourceforge.net/projects/libusb-win32/files/latest/download?source=files

`include/lusb0_usb.h` to `C:\Qt\5.6\Tools\mingw492_32\include`		
`lib/gcc/libusb.a` to `C:\Qt\5.6\Tools\mingw492_32\lib`

### 5. DevkitPro
Download and install: https://sourceforge.net/projects/devkitpro/files/latest/download?source=files

You only need devkitARM, nothing more (no extra lib or anything else) to compile the firmware (ARM) side. Assuming you installed it to `C:\devkitpro`, make sure you set the `DEVKITARM` environment variable to `/c/devkitPro/devkitARM` and add its bin to your PATH:		
`export DEVKITARM=/c/devkitPro/devkitARM`		
`export PATH=$PATH:$DEVKITARM/bin`

### 6. Install Strawberry Perl
Download and install: https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/strawberry-perl/strawberry-perl-5.10.1.3.msi

### 7. Build and run
Download and install Git for Windows: https://git-scm.com/download/win

- Run minimal system: `C:\Qt\msys\msys.bat`

- Set the environment:		
`export DEVKITARM=/c/devkitPro/devkitARM`		
`export PATH=$PATH:$DEVKITARM/bin`		
`export QTDIR=/c/Qt/5.6/mingw49_32`		
`export PATH=$PATH:$QTDIR/bin`

- Clone iceman fork		
`git clone https://github.com/iceman1001/proxmark3.git`

- Get the latest commits	
`git pull`

- CLEAN COMPILE		
`make clean && make all`

Assuming you have Proxmark3 Windows drivers installed you can run the Proxmark software where "X" is the com port number assigned to proxmark3 under Windows. 
	
- Flash the BOOTROM		
`client/flasher.exe comX -b bootrom/obj/bootrom.elf`

- Flash the FULLIMAGE	
`client/flasher.exe comX armsrc/obj/fullimage.elf`
	
- Change into the client folder		
`cd client`
	
- Run the client	
`proxmark3.exe comX`

##Buying a proxmark3
The Proxmark 3 device is available for purchase (assembled and tested) from the following locations:

   * http://proxmark3.tictail.com/ (For buyers in EU, most likely in Sweden)
 
   * http://www.elechouse.com/  (new and revised hardware package 2015, located in China)  


##Enjoy

January 2015, Sweden
iceman at host iuse.se




##Note from Jonathan Westhues
Most of the ultra-low-volume contract assemblers could put
something like this together with a reasonable yield. A run of around
a dozen units is probably cost-effective. The BOM includes (possibly-
outdated) component pricing, and everything is available from Digikey
and the usual distributors.

If you've never assembled a modern circuit board by hand, then this is
not a good place to start. Some of the components (e.g. the crystals)
must not be assembled with a soldering iron, and require hot air.

The schematics are included; the component values given are not
necessarily correct for all situations, but it should be possible to do
nearly anything you would want with appropriate population options.

The printed circuit board artwork is also available, as Gerbers and an
Excellon drill file.


LICENSING:

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA


Jonathan Westhues
user jwesthues, at host cq.cx

May 2007, Cambridge MA
