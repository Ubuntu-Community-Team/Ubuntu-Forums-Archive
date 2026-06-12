---
title: "iButton/1-Wire"
date: 2006-07-21
forum: The Cafe
---

### Post by Xaruan on 2006-07-21
I don't know how many people have heard of it, but iButtons are small devices able to take different readings (such as temperature and humidity).  My research lab is hoping to get some of these to monitor our linux cluster room (so our 40-some computers don't overheat).

I was just wondernig if anyone has come across software to allow linux (ubuntu, specifically) to work with iButtons.  It's unfortunate the ibutton kits that are sold are only intended for PCs.


Thanks for any help.



(Ubuntu = best linux community)

---

### Post by Paerez on 2006-07-21
i found this on google:
[http://www.missl.cs.umd.edu/~tfraser/HOWTOs/ibutton_install.html](http://www.missl.cs.umd.edu/~tfraser/HOWTOs/ibutton_install.html)

---

### Post by Xaruan on 2006-07-21
Thanks.  I'll b giving this a try.

---

### Post by mlissner on 2009-02-10
I'd be interested in hearing if anybody has gotten these to work under Linux. I'm struggling with mine despite the fact that it's ridiculously old tech, and ought to work without any issues whatsoever.

Any help?

---

### Post by spike the jackal on 2009-09-04
I've used these babies for research starting about a year ago.
Maxim has a good deal of [software]("http://www.maxim-ic.com/products/ibutton/software/resources.cfm") (they have a public domain kit).

The drivers *are* in the kernel as I recall. I  was able to get real time readings but have not been able to read the log or reconfigure the devices. I ended up reading my iButtons through a windows virtual machine, using the java reader.

Update:
I just checked the public domain kit. It's a new version as precompiled binaries and/or source code. It may be worth your time to [check em out]("http://www.maxim-ic.com/products/ibutton/software/1wire/wirekit.cfm").

---

### Post by capt.tagon on 2009-12-15
You can use the Java OneWireViewer, but it expects librxtx-java support to be installed and will only work with the DS9097U Serial to One-Wire bridge.

I've got the DS9490R USB to One-Wire bridge to work under OWFS, it seems to expose all the iButton stuff pretty well, but this is kind of a clunky way to do things. After writing some extensive scripting, you might be able to set a thermochron up, save a mission and then retrieve data. Which is all straight forward using the Java interface...

---

### Post by cafeschintze on 2010-03-26
If there are any news on this I would be VERY interested.

I have the [DS9490B]("http://www.fuchs-shop.com/img/products/200x150/ds9490b.jpg") adapter and installed the librxtx-java package from respositories. However, using the maxim 1-wire java app it says, it is looking for the [DS9097U]("http://www.fuchs-shop.com/de/view/product/13372119/").

Am I right, that the problem is within the rxtx, which doesn't support usb?

---

### Post by Spike the Dingo on 2010-06-08
Sounds like it. I'd be really interested if we can get this working on linux. (I'm Spike the Jackal)

---

### Post by linuxonbute on 2010-08-14
I have just started playing with an ibutton (a DS1921G) and a DS9490 running kernel 2.6.31-22-generic. 
I am running owfs with some python scripts. At the moment I am just able to get the current temperature and it all has to be using sudo so there is some way to go. It's my first time with fuse which owfs uses and I need to figure out why I have to use sudo for every command. The code I have so far is 

```

sudo /opt/owfs/bin/owfs -F -u -m /home/norman/1-wire

```
which sets up the fuse file access to the ibutton

```


#! /usr/bin/env python

# $Id: one_wire_sensors.py 23 2004-07-22 04:35:36Z peter $
#
# need to check for /1-wire mounted but Vendor=04fa is not
# in the usb usb devices file. this can occur when the usb
# dongle is no longer connected.
#
# check that /1-wire is mounted
# if not, check that Vendor=04fa is in the usb devices file.
# if it is, then kick /etc/init.d/owfs to start up again
# if not, then ?


import os
import syslog
import csv
import time
##import util


Debug           = True
OWUSBVendor     = '04fa'
USBDevices      = '/home/norman/1-wire/21.B5fb22000000/temperature'
MountFile       = '/proc/mounts'
OWUSBMount      = '/home/norman/1-wire/21.B5fb22000000/temperature'
MountCommand    = '/etc/init.d/owfs.init start'
UnmountCommand  = '/etc/init.d/owfs.init stop'
SensorLogName   = 'sensor.log'
Sensors         = {
    'Temperature1' : os.path.join( OWUSBMount, '10.B7B64D000800' ),
    'Temperature2' : os.path.join( OWUSBMount, '10.54BA4D000800' ),
    #'Humidity1'   : os.path.join( OWUSBMount, '12.386623000000' ),
    #'Humidity2'   : os.path.join( OWUSBMount, '12.3B6F23000000' ),
   }
Messages        = {
    'MountedNoPresence' :
    '1-wire mounted but no usb presence, unmounting 1-wire',

    'UnmountedPresence' :
    '1-wire not mounted but usb presence, mounting 1-wire',

    'UnmountedNoPresence' :
    '1-wire not mounted and no usb presence, nothing can be done',

    'MountedNoSensors' :
    '1-wire mounted and usb presense but no sensors, remounting 1-wire',
    }


def log_message( message ):
    if Debug:
        print message
    syslog.syslog( syslog.LOG_DAEMON|syslog.LOG_WARNING, message )


def check_mount( mount_point ):
    known_mounts = open( MountFile, 'r' ).readlines()
    for mount in known_mounts:
        if mount_point in mount:
            return True
    return False


def check_usb_vendor( vendor ):
    usb_lines = open( USBDevices, 'r' ).readlines( )
    vendor = 'Vendor=' + vendor
    for line in usb_lines:
        if vendor in line:
            return True
    return False


def check_sensors( ):
    for sensor in Sensors:
        if not os.path.isdir( Sensors[ sensor ] ):
            return False
    return True


def read_temperature( ):
    path = os.path.join( Sensors[ 'Temperature1' ], 'temperature' )
    temperature1 = open( path, 'r' ).readlines( )
    path = os.path.join( Sensors[ 'Temperature1' ], 'temperature' )
    temperature2 = open( path, 'r' ).readlines( )
    return ( float( temperature1[ 0 ] ), float( temperature2[ 0 ] ) )


def log_sensors( ):
    current_time = time.time( )
    path = util.log_path( '', SensorLogName )
    temperature1, temperature2 = read_temperature( )
    writer = csv.writer( file( path, 'a' ) )
    writer.writerow( ( current_time, temperature1, temperature2 ) )


def one_wire( ):
    mounted      = check_mount( OWUSBMount )
    usb_presence = check_usb_vendor( OWUSBVendor )
    sensors      = check_sensors( )

##    if mounted:
##        if not usb_presence:
##            log_message( Messages[ 'MountedNoPresence' ] )
##            os.system( UnmountCommand )
##        elif not sensors:
##            log_message( Messages[ 'MountedNoSensors' ] )
##            os.system( UnmountCommand )
##           os.system( MountCommand )
##        elif Debug:
##            print 'all is right with the world'
##    elif usb_presence:
##        log_message( Messages[ 'UnmountedPresence' ] )
##        os.system( MountCommand )
##    else:
##        log_message( Messages[ 'UnmountedNoPresence' ] )


if __name__ == '__main__':
    one_wire( )
    if check_mount( OWUSBMount ):
        log_sensors( )

```

This is code I found here: [http://www.pyzine.com/Issue007/Section_Articles/article_MobileDataCollection.html](http://www.pyzine.com/Issue007/Section_Articles/article_MobileDataCollection.html)

I saved it as readbutton.py and run it with sudo again.
All the lines with ## at the beginning are lines I had to comment out so it would run. Mainly because I had access errors otherwise.

Then 
```

sudo cat 1-wire/21.B5fb22000000/temperature

```
to see the current value held in the ibutton.

Hope this helps and maybe someone can help me get it all working fully. I could not find the util module anywhere nor would it work without sudo. I am a member of the fuse group but all I see for the 1-wire directory is 
d?????????  ? ?      ?               ?                ? 1-wire

---

### Post by linuxonbute on 2010-08-14
Ok 

add the lines :
user_allow_other
allow_other

to /etc/fuse.conf

also note that:

```

sudo /opt/owfs/bin/owfs -F -u -m /home/norman/1-wire

```

should be :
```

/opt/owfs/bin/owfs --allow_other -F -u -m /home/norman/1-wire

```

then no need for sudo.

---

### Post by Dustin2128 on 2010-08-14
this thread= necromancy exhibit A.

---

### Post by mlissner on 2010-08-15
> **Dustin2128 said:**
> this thread= necromancy exhibit A.
True, but I'm pretty excited to see that /somebody/ finally got these things to work in Linux. I still have about ten iButtons that were one of the VERY last things that I ever needed Windows for, and this is awesome.

I hope that this thread can be revived again and again, if it means getting these things to work properly.

---

### Post by Austin25 on 2010-08-15
Well, I believe you can interface them with Arduinos, and the Arduino IDE is for Ubuntu. Does that help?

---

### Post by linuxonbute on 2010-08-15
> **Austin25 said:**
> Well, I believe you can interface them with Arduinos, and the Arduino IDE is for Ubuntu. Does that help?

I am sure you can but this code is only the first stuff I have done and it just took a few hours to get this far. A simple addition to a bit of python code allows me to read the temp from an ibutton every minute/hour/day at will. Also these buttons I have can be programmed to start recording up to 2048 individual temps spaced out between, i think, every minute to every 255 minutes. They do this independently so you can put them in your fridge, greenhouses or elsewhere and then at any time afterwards you can retrieve them and plug them into your computer then read the values back. i want to do something like that so will be working on it when I next get time.

---

### Post by mlissner on 2010-08-15
Yeah, I used them to create the project here: [http://michaeljaylissner.com/pct-temperatures](http://michaeljaylissner.com/pct-temperatures) (warning: Java applet).

What I want would be a way to read them and program them via command line or GUI. If you could make such a thing, that would be phenomenal.

---

### Post by linuxonbute on 2010-08-19
Well I have made some progress.

I am running Ububtu 9.10 and did the following:

1/  
installed gvfs-fuse, fuse-utils, python-fuse, checkinstall and swig using synaptic package manager.

2/     Downloaded owfs-2.8p1.tar.gz from [http://sourceforge.net/projects/owfs/files/](http://sourceforge.net/projects/owfs/files/)
	changed to directory it was downloaded to then unpacked it with tar xvzf owfs-2.8p1.tar.gz

3/     configured and installed it as follows:

	cd owfs-2.8p1
	./configure
	sudo checkinstall ( accepted default options )

This installed the needed files to /opt/owfs with the binary files in /opt/owfs/bin

Then you need to edit /etc/fuse.conf as root and add the lines

user_allow_other
allow_other

then create a directory for fuse/owfs to mount the files.

I created 1-wire in the root of my home area

There are then 2 ways to view the data in the ibutton.

1/ launch owfs with the following command:   /opt/owfs/bin/owfs --allow_other -C -u -m /home/norman/1-wire

where --allow_other allows any user to access the files, -C says display temperatures as centigrade -u means find the button via usb and -m tells it where to mount the files.

This gives the following: 
ls -l ~/1-wire
drwxrwxrwx 1 root root  8 2010-08-19 17:03 21.B5FB22000000
drwxrwxrwx 1 root root  8 2010-08-19 17:03 81.FC582B000000
drwxr-xr-x 1 root root  8 2010-08-19 15:58 alarm
drwxr-xr-x 1 root root  8 2010-08-19 15:58 bus.0
drwxr-xr-x 1 root root  8 2010-08-19 15:58 settings
drwxrwxrwx 1 root root  8 2010-08-19 17:03 simultaneous
drwxr-xr-x 1 root root  8 2010-08-19 15:58 statistics
drwxr-xr-x 1 root root 30 2010-08-19 15:58 structure
drwxr-xr-x 1 root root  8 2010-08-19 15:58 system
drwxr-xr-x 1 root root  8 2010-08-19 15:58 uncached

21B5FB22000000 is my ibutton ( this is a unique number - yours will be different ) so
 ls /home/norman/1-wire/21.B5FB22000000/
about    alarm_dow   alarm_minute  alarm_state    alias  crc8    histogram  locator  memory   overtemp  r_address  r_locator  temperature  undertemp    address  alarm_hour  alarm_second  alarm_trigger  clock  family  id         log      mission  pages     r_id       set_alarm  type

Some of these are files and some directories. ls log gives masses of information including every one of the 2048 temperature readings it can take during a 'mission'

A simple python script to demonstrate this is :

```

#!/usr/bin/python

import os
m = 0

while m < 2048:

	myval = '/home/norman/1-wire/21B5FB22000000/log/temperature.' + str(m)
	fp = open(myval, 'r')
	pt = fp.readline()
	print (pt)
	fp.close()
	m += 1
	fp.close()


```
will display all the values in them.


2/  Instead launch owhttpd:

/opt/owfs/bin/owhttpd -u -p 4444

then fire up your browser and point it to :

[http://localhost:4444](http://localhost:4444)

and browse through it from there.

You can set up and start a mission from the web page by alltering some of the contents.

I need to figure out what I need to set the contents of various files to so as to be able to set up a mission from the command line and 
other bits which I am interested in.

---

### Post by mlissner on 2010-08-19
Incredible. I can't wait to try this out next time I'm going on a trip. Thanks for all the details and hard work. Please, please keep us posted with anything else you figure out, because this is an issue that as far as I know, has never been sorted out on Linux, and if it has, it's never been documented.

---

### Post by linuxonbute on 2010-08-19
> **mlissner said:**
> Incredible. I can't wait to try this out next time I'm going on a trip. Thanks for all the details and hard work. Please, please keep us posted with anything else you figure out, because this is an issue that as far as I know, has never been sorted out on Linux, and if it has, it's never been documented.
Well thanks, but apart from the little bit of python most of it is stuff I gathered from a few dozen google searches. I picked up tiny a bit here and there and just played about with them until I got it working on the web, got a mission started and then tried the python code.

>>>> Code Update <<<<
```

#!/usr/bin/python
"""
::BOH
Code to read logged temperature with the corresponding date and time
from an ibutton with it mounted to a fuse file system.
this code for what it's worth is released under the gpl
::EOH 
"""

m = 0
counter = 200

while m < counter:

	myval = '/home/norman/1-wire/21B5FB22000000/log/temperature.' + str(m)
	mytime = '/home/norman/1-wire/21B5FB22000000/log/date.' + str(m)
	fptemp = open(myval, 'r')
	ptemp = fptemp.readline()
	fptime = open(mytime, 'r')
	ptime = fptime.readline()
	mx = ptime + "  - " + ptemp
	print (mx)
	fptemp.close()
	fptime.close()
	m += 1

```

---

### Post by Austin25 on 2010-08-20
Ok, maybe I didn't help. OK, sorry. My bad.

---

### Post by linuxonbute on 2010-08-22
> **mlissner said:**
> Yeah, I used them to create the project here: [http://michaeljaylissner.com/pct-temperatures](http://michaeljaylissner.com/pct-temperatures) (warning: Java applet).

What I want would be a way to read them and program them via command line or GUI. If you could make such a thing, that would be phenomenal.

I had a look at your excellent project and wonder if you can tell me how you set up the ibuttons to only record the temperature every hour. Everything I have looked at so far has drawn a blank. I have been unable to change what seems to be the default sampling rate of 1 per minute. Otherwise I think I have got all I need to start coding for command line and then look at GUI stuff.

---

### Post by linuxonbute on 2010-08-26
> **linuxonbute said:**
> I had a look at your excellent project and wonder if you can tell me how you set up the ibuttons to only record the temperature every hour. Everything I have looked at so far has drawn a blank. I have been unable to change what seems to be the default sampling rate of 1 per minute. Otherwise I think I have got all I need to start coding for command line and then look at GUI stuff.

Well I found out how to do this. After looking at a few things I found there is a bug in the code. In the virtual file system (/path-to/1-wire)
mission/frequency is set up for yes/no input. It should be unsigned int so I edited the code in ow1921.c and re-compiled. Now it is possible to set missions up to change time between samples. I have informed the maintainers so I hope this will be squashed in the next version.

I think I have everything I need to start some more coding and once I get it working I will set up a page on my web site.

---

### Post by Grenage on 2010-08-26
This *may* be of interest to anyone looking into this stuff.

I rigged up temperature sensors to feed into Nagios, but I built the readers with DS18S20 sensors.  It's very easy, and can be polled with digitemp.

[http://martybugs.net/electronics/tempsensor/](http://martybugs.net/electronics/tempsensor/)
[http://www.hoppie.nl/tempsens/](http://www.hoppie.nl/tempsens/)

---

### Post by linuxonbute on 2010-09-24
Just a small update. owfs2.8p2 has my small mod included. 
I am now running ubuntu 10.04 and have owfs set up and running with it. 
At present owfs needs python 2.4 to run and this is not included with 10.04. 
I found this did it: [http://automation.binarysage.net/?p=1244&cpage=1#comment-169](http://automation.binarysage.net/?p=1244&cpage=1#comment-169)
BUT >> before << I added the Karmic repositories I did :
apt-get install \
automake \
autoconf \
autotools-dev \
gcc \
g++ \
libtool \
libusb-dev \
fuse-utils \
libfuse-dev \
swig \
tcl8.4-dev \
php5-dev

Then added the Karmic stuff and at the point where it says:
apt-get install \
automake \
autoconf \
autotools-dev \
gcc \
g++ \
libtool \
libusb-dev \
fuse-utils \
libfuse-dev \
swig \
python2.4-dev=2.4.6-1ubuntu3.2.9.10.1 \
tcl8.4-dev \
php5-dev

I only did:
apt-get install python2.4-dev=2.4.6-1ubuntu3.2.9.10.1

I then removed the Karmic repositories once again.

Then followed the rest of the instructions.

I have done a little python coding which creates a directory for the 1wire virtual file system, 
one for the config files i will be creating later and starts owfs if it needs to.
It can be run each time you want to - just plug in your ibutton first.
```

#!/usr/bin/python
"""
::BOH
 Copyright (c) 2010 Norman Elliott. All rights reserved.
 This program or module is free software: you can redistribute it and/or
 modify it under the terms of the GNU General Public License as published
 by the Free Software Foundation, either version 2 of the License, or
 version 3 of the License, or (at your option) any later version. It is
 provided and is distributed in the hope that  it will be useful, but 
 WITHOUT ANY WARRANTY; without even the implied  warranty of 
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. 
 See the GNU General Public License for more details.
::EOH
"""
import os
import sys
import subprocess

#find users home directory
basedir = os.path.expanduser("~")

#set up 1wire and button directories in root of home directory
buttondir = basedir + "/button"
wiredir = basedir + "/1-wire"
try:
	os.system("clear")
except ValueError:
	print "Houston we have a problem with permissions"
print "                Setting up your ibutton"
try:
	os.mkdir( buttondir)
	print "\nmaking Button directory"
except OSError, e:
	if e.errno == 17 and os.path.isdir(buttondir):
		print "\nButton directory exists"
	else:
		raise

try:
	os.mkdir( wiredir)
	print "\nmaking wire directory"
except OSError, e:
	if e.errno == 17 and os.path.isdir(wiredir):
		print "\n1-wire directory exists"
	else:
		raise
#check if owfs is running and, if not, start it up
print "\nDirectories in place so now checking if owfs is running\n"


procdir = buttondir + "/process.txt"

while True:
	try:
		os.system("ps ax" ">$HOME/button/process.txt")
		break
	except ValueError:
		print"\nCannot get process list\n"
found = 0
fo = open(procdir, 'r')

for line in fo:
	p = line
	q = p.find("owfs")
	if q != -1 :
		found = 1
			
if found == 1:
	print "owfs is already running"
else:
	print "Starting owfs\n"
	while True:
		try:
			os.system("/opt/owfs/bin/owfs " "--allow_other " "-C " "-u " "-m " "$HOME/1-wire")
			break
		except ValueError:
			print"\nCannot start owfs\n"

#Find your ibutton and display it's id
print "\nFinding your ibutton\n and creating the config file for it"
directory = basedir + "/1-wire"
buttonconfig = basedir + "/button/mybutton.cfg"
bf=open(buttonconfig, 'w')
for name in os.listdir(directory):
	if os.path.isdir(os.path.join(directory, name)):
		if name[0:2] == "21":
			print "\n\033[34m>  Found ibutton " + name  + "  <\033[0m\n"
			bf.write(name)


bf.close()

```

I am now working on a GUI program to talk to the ibutton so as to set up a 'mission'. Also one to display the various results although it might take some time.

In the meantime the code above will report what your ibutton is and you can plug it into the code from post #18. 
Setting counter to any value between 1 and 2048 to see the times and corresponding temperature stored.

---

### Post by linuxonbute on 2011-03-01
Well i have now got a little further with this. I have set up a page on my website with the information i have so far. 

I asked Mike Lissner to try it out initially but he has not been able to even get the usb access to work yet. 

I have emailed him my new udev rule so it might fix his problem but if not maybe if he posts his problem here someone might be able to resolve it for him.

In any case if anyone wants to try my tentative 'Howto' then please feel free to do so and let me know how you get on. Of course if anyone knows python they might like to improve my work. ( that would not be hard to do! )

[http://www.nelliott.co.uk/linux](http://www.nelliott.co.uk/linux)

best wishes,
norman

---

### Post by mlissner on 2011-03-07
Well, "mlissner" was supposed to be a pseudonym, but I guess my cover is blown.

In any case, I won't have time to look at this for a while. Anybody else game to give linuxonbute's solution a try? 

It'd be amazing to get this working at last.

---

### Post by thakk on 2011-10-03
Well I will have a shot at necroing this thread, since I am just getting my hardware working under 11.04.

Out of the box, digitemp seems to be quite easy.

I have the LinkUSB from ibuttonlink.com
I have 1 DS18B20P hooked up to the cable.

#apt-get install digitemp rrdtool mysql-server

# ln -s /usr/bin/digitemp_DS9097U /usr/bin/digitemp

#digitemp -i -c /etc/digitemp.conf -s /dev/ttyUSB1 

(my linkUSB is on USB1 because I have another device for my home automation on USB0)

Now to take a reading

#digitemp -q -c /etc/digitemp.conf -a

Oct 03 20:51:20 Sensor 0 C: 23.69 F: 74.64

This should get you guys started with digitemp pretty easily. I switched to Ubuntu from CentOS because I've had better luck finding the software I want to work with Ubuntu.

-=/>Thom

---

