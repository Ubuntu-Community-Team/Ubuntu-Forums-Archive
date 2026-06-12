---
title: "HOWTO Set-up Pinnacle PCTV (pro) Serial Remote &amp; lirc"
date: 2011-01-04
forum: Tutorials
---

### Post by SpiderSkull on 2011-01-04
This tutorial works with ubuntu 9.10, 10.04, 10.10, 11.04, 11.10.
This howto is for the Pinnacle PCTV (pro) serial remote.
Also a little howto on how to use this remote with XBMC Eden.

[IMG]http://giannakopoulos.eu/img//pinnaclesyspctvremote.jpg[/IMG]

First we have to download lirc: [http://www.lirc.org/](http://www.lirc.org/).
Download version 0.8.6 (on the left).
Download it to your Download folder and extract it there.

Now open an console.
Log in as root
```
sudo -s
```

No CD to the lirc folder.
```
cd /home/"username"/Downloads/lirc-0.8.6/
```

Now we need to configure lirc.
```
./configure
```

Select option "1. Driver Configuration".
Now a new menu will open. Select option "4. Other serial port devices".
Then select "Pinnacle Systems PCTV (pro) reciever" you have to scroll a bit for this.
Now select the com port where the IR is connected. If you don know select "/dev/ttyS0"

Select option "2. Software Configuration",
and select "1. Compile tools for X-Windows" and "5. Use syslog instead of own log file".

Select option "3. Save configuration & Run configure".

Now lirc says you need to run make & make install, DON'T DO THIS!
We need to install lirc from the repository's first.

```
apt-get install lirc
```

Now we need to select the device.
Select "Pinnacle Systems PCTV (pro) reciever"

Now the IR transmitter.
Select "Serial Port (UART) : Direct TV Reciever"

Now we need to stop the Lirc service.
and kill al remaining stuff of lircd

```

service lirc stop
rm /var/run/lirc/*

```

Now enter make & make install (watch the dubble &&).

```
make && make install
```

Now edit the file /etc/lirc/hardware.conf.

```
gedit /etc/lirc/hardware.conf
```

Change te following lines:

REMOTE_DRIVER="pinsys"
REMOTE_DEVICE="/dev/ttyS0"       # (for COM1, for COM2 /dev/ttyS1 and so on).

TRANSMITTER_DEVICE="/dev/lirc"

LOAD_MODULES="false"

Now we need to copy some files to the right place.

```

cp /usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv /etc/lirc/lircd.conf
cp /usr/local/sbin/* /usr/sbin/

```

Now we have to reconfigure setserial.

```
dpkg-reconfigure setserial
```

Set setserial to manuel.
Edit the file autoserial.conf and delete serial.conf

```

rm /etc/serial.conf
gedit /var/lib/setserial/autoserial.conf

```

Remove all the lines from autoserial.conf except the line where stands /dev/ttyS0 or if you used COM2 /dev/ttyS1. You don't have to delete the comment lines (#).

Start lirc service again.
and start testing configuration.

NOTE! For Ubuntu 11.10 this will not work! Restart computer for changes to take effect!
```

service lirc start
irw

```

now press some buttons on your remote.
If it is ok you should see something like this: (if not just reboot computer and then try irw)

> 
000000000000001b 00 vol+ PinnacleSysPCTVRemote
000000000000000b 00 Stop PinnacleSysPCTVRemote
0000000000000015 00 Pause PinnacleSysPCTVRemote
000000000000000d 00 Play PinnacleSysPCTVRemote


I used XBMC as test program. XBMC has build-in lirc support your remote should work in xbmc.

```

add-apt-repository ppa:team-xbmc
apt-get update

// For ubuntu 11.10:
apt-get install xbmc

// For older ubuntu:
apt-get install xbmc xbmc-standalone

```

For XBMC Eden this remote doesn't work directly anymore to change this:
edit /usr/share/xbmc/system/Lircmap.xml
```

gedit /usr/share/xbmc/system/Lircmap.xml

```

Look for the line that says <remote device="PinnacleSysPCTVRemote">
and change the lines according to this:
```

       <remote device="PinnacleSysPCTVRemote">
                <play>KEY_PLAY</play>
                <pause>KEY_PAUSE</pause>
                <stop>KEY_STOP</stop>
                <forward>KEY_FASTFORWARD</forward>
                <reverse>KEY_REWIND</reverse>
                <left>Vol-Rew</left>
                <right>Vol+FF</right>
                <up>Chan+Play</up>
                <down>Chan-Stop</down>
                <pageplus>KEY_CHANNELUP</pageplus>
                <pageminus>KEY_CHANNELDOWN</pageminus>
                <select>middle</select>
                <back>KEY_UNDO</back>
                <menu>KEY_MENU</menu>
                <title>KEY_L</title>
                <info>KEY_INFO</info>
                <skipplus>KEY_NEXT</skipplus>
                <display>Fullscreen</display>
                <record>KEY_RECORD</record>
                <volumeplus>KEY_VOLUMEUP</volumeplus>
                <volumeminus>KEY_VOLUMEDOWN</volumeminus>
                <mute>KEY_MUTE</mute>
                <power>KEY_POWER</power>
                <one>KEY_1</one>                
                <two>KEY_2</two>
                <three>KEY_3</three>
                <four>KEY_4</four>
                <five>KEY_5</five>
                <six>KEY_6</six>
                <seven>KEY_7</seven>
                <eight>KEY_8</eight>
                <nine>KEY_9</nine>
                <zero>KEY_0</zero>
        </remote> 

```
Now your remote also works in XBMC Eden :)

For help you can mail me, or use the forum.

---

### Post by viaggiatore on 2011-01-28
This tutorial is perfect. Thank you O:)

I tried it with ubuntu 10.10 and Lirc 0.8.7 and it also works O:)

---

### Post by SpiderSkull on 2011-04-13
Refer to a question I had,

Ubuntu 9.04 / 9.10 are using lirc 0.8.6.
Ubuntu 10.04 / 10.10 are using lirc 0.8.7.
Ubuntu 11 uses lirc 0.9.0.

This document is working for al versions above (replace the version in the document, by the one that your ubuntu version needs).

Greetings.

---

### Post by dtzortzis on 2012-01-02
This is working for me in Ubuntu 10.10. 
Lot's of love,
thank you!!

:P

---

### Post by Statia on 2012-08-03
This HOWTO is no longer current. It does not work on 12.04 with the current version of lirc, 0.9.

```
# ./configure
dialog not found!
Please read the documentation!!!

# ./setup.sh 
dialog not found!

# ./install-sh 
./install-sh: no input file specified.

# ./data2setup.sh 
./data2setup.sh: line 4: setup-functions.sh: No such file or directory
# this file was generated by calling ./data2setup.sh 
# DO NOT EDIT

./data2setup.sh: line 10: setup_seq_init: command not found
./data2setup.sh: line 11: gen_hw_type_menu: command not found


```

---

### Post by Statia on 2012-08-03
I tried with 0.8.6, same result:

```
root@quokka:/home/statia/Downloads/lirc-0.8.6# ./configure
dialog not found!
Please read the documentation!!!
```

---

### Post by Statia on 2012-08-03
Also, there is no /etc/serial.conf on the system, and /var/lib/setserial/autoserial.conf contains no lines about /dev/ttySn, only:

```
#
###PORT STATE GENERATED USING AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE-ONCE###
###AUTOSAVE###
#
# If you want to configure this file by hand, use 
# dpkg-reconfigure setserial
# and change the configuration mode of the file to MANUAL. If you do not do this, this file may be overwritten automatically the next time you upgrade the
# package.
#
```

---

### Post by Statia on 2012-08-03
And (hopefully) finally:

```
root@quokka:/etc# dpkg-reconfigure setserial
update-rc.d: warning: etc-setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
update-rc.d: warning: setserial stop runlevel arguments (0 6) do not match LSB Default-Stop values (0 1 6)
```Tomorrow I'm going to install the serial cable on my motherboard and I can start testing. If I can get it to work, I hope I can recall what I did and try to update this HOWTO.

---

### Post by Statia on 2012-08-03
Instead of the ./configure method of the original HOWTO, I tried dpkg-reconfigure lirc:

```
$ sudo dpkg-reconfigure lirc
ls: cannot access /lib/modules/3.2.0-27-generic/kernel/drivers/staging/lirc: No such file or directory
```So I have no modules?
Well, I also found this tutorial:

[URL="http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install"]http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install
[/URL]
which advises to install modules:

```
sudo apt-get install lirc lirc-modules-source module-assistant
```On my system:
```
Package lirc-modules-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lirc:i386 lirc

E: Package 'lirc-modules-source' has no installation candidate
```

---

