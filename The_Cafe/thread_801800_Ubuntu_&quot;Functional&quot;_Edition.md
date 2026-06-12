---
title: "Ubuntu &quot;Functional&quot; Edition"
date: 2008-05-20
forum: The Cafe
---

### Post by Scheater5 on 2008-05-20
I recently posted a thread in the section formally known as the backyard (I just can't get used to "omg pink ponies"...) called "[Ubuntu Bloated Edition]("http://ubuntuforums.org/showthread.php?t=795453")" about a heavyweight variant of Ubuntu.  The word "bloated" was meant tongue-in-cheek, but apparently it turned a bunch of people off, and I got nothing but negative reactions to it.  I still think it would be a good idea, so I tried the script idea.  I've got a few questions though:
I would like to give the user the option to install XBMC or Elisa if they chose (the option to install either, both, or neither).  How might I do this?
I would like to install hamachi-gui.  Is there any way to tell what the architecture of the install is (x86, amd64) and then pass that on to wget so it downloads the right version?  
Does anyone see any issues related to running the entire thing as root, like permissions or directory problems?  

Yet to do are the changes to Compiz default settings I mentioned in the "Bloated Edition" thread, determining the graphics card and then installing the appropriate configuration gui, configuring avant and the changes to the panel.  I don't know how to do any of these.  

I am aware of the fact there are some things illegal in most countries.  Run at your own risk.  Here is what I have so far. If anyone is interested, I would love is other people would test it, or at least take a look and see if there are any problems/things you would change.


# Check if the script is being run as root exit if it is not.
if [ "$UID" -ne "0" ]
then
echo "[ERROR] This script must be run as root"
exit 1
fi
mv /etc/apt/sources.list /etc/apt/sources.list_backup
echo "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse" > /etc/apt/sources.list
echo "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse" > /etc/apt/sources.list
echo "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse" > /etc/apt/sources.list
echo "deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse" > /etc/apt/sources.list
echo "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner" > /etc/apt/sources.list
mkdir /etc/apt/sources.d
echo "deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main" > /etc/apt/sources.list.d/sources.list
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free" > /etc/apt/sources.list.d/sources.list
echo "deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main" > /etc/apt/sources.list.d/sources.list
apt-get install -y ubuntu-restricted-extras
wget [http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz](http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz)
tar xfz hamachi-0.9.9.9-20-lnx.tar.gz
cd hamachi-0.9.9.9-20-lnx
make install
./tuncfg/tuncfg
cd ..
cp ./hamachi /usr/bin
hamachi-init
echo "tun" > /etc/modules
apt-get -y install libdvdread3 
/usr/share/doc/libdvdread3/install-css.sh
apt-get install -y install totem-xine
apt-get install -y install libdvdcss2
cd ~
wget [http://packages.linuxmint.com/pool/import/s/sunbird/sunbird_0.8-mint1_all.deb](http://packages.linuxmint.com/pool/import/s/sunbird/sunbird_0.8-mint1_all.deb)
dpkg ./sunbird_0.8-mint1_all.deb
apt-get install thunderbird
apt-get install avant-window-navigator-trunk avant-window-navigator-data-trunk awn-extras-applets-trunk awn-manager-trunk libawn0-trunk python-awn-trunk vala-awn-trunk
apt-get install vsftpd
wget [http://www.voxpopulimedia.com/pub/howto/homenetworking/vsftpd.conf](http://www.voxpopulimedia.com/pub/howto/homenetworking/vsftpd.conf)
mv -f vsftpd.conf /etc/vsftpd.conf
apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan
wget [http://www.voxpopulimedia.com/pub/howto/homenetworking/ftp.service](http://www.voxpopulimedia.com/pub/howto/homenetworking/ftp.service)
sudo mv --force --target-directory=/etc/avahi/services/ ftp.service
sudo /etc/init.d/avahi-daemon restart

---

### Post by Sef on 2008-05-20
Moved to Community Cafe.

---

### Post by FuturePilot on 2008-05-20
```
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse" > /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse" > /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse" > /etc/apt/sources.list
echo "deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse" > /etc/apt/sources.list
echo "deb http://archive.canonical.com/ubuntu hardy partner" > /etc/apt/sources.list
```
Will only leave you with
```
deb http://archive.canonical.com/ubuntu hardy partner
```
In your sources.list
You need to use
```
>>
``` to append

---

### Post by Scheater5 on 2008-05-20
Thank you much FuturePilot.
There's not much use in it, but here is the revised script.  
```
# Check if the script is being run as root exit if it is not.
if [ "$UID" -ne "0" ]
then
echo "[ERROR] This script must be run as root"
exit 1
fi
mv /etc/apt/sources.list /etc/apt/sources.list_backup
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://archive.canonical.com/ubuntu hardy partner" >> /etc/apt/sources.list
mkdir /etc/apt/sources.d
echo "deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main" >> /etc/apt/sources.list.d/sources.list
echo "deb http://packages.medibuntu.org/ hardy free non-free" >> /etc/apt/sources.list.d/sources.list
echo "deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main" >> /etc/apt/sources.list.d/sources.list
apt-get install -y ubuntu-restricted-extras
wget http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz
tar xfz hamachi-0.9.9.9-20-lnx.tar.gz
cd hamachi-0.9.9.9-20-lnx
make install
./tuncfg/tuncfg
cd ..
cp ./hamachi /usr/bin
hamachi-init
echo "tun" > /etc/modules
apt-get -y install libdvdread3 
/usr/share/doc/libdvdread3/install-css.sh
apt-get install -y install totem-xine
apt-get install -y install libdvdcss2
cd ~
wget http://packages.linuxmint.com/pool/import/s/sunbird/sunbird_0.8-mint1_all.deb
dpkg ./sunbird_0.8-mint1_all.deb
apt-get install thunderbird
apt-get install avant-window-navigator-trunk avant-window-navigator-data-trunk awn-extras-applets-trunk awn-manager-trunk libawn0-trunk python-awn-trunk vala-awn-trunk
apt-get install vsftpd
wget http://www.voxpopulimedia.com/pub/howto/homenetworking/vsftpd.conf
mv -f vsftpd.conf /etc/vsftpd.conf
apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan
wget http://www.voxpopulimedia.com/pub/howto/homenetworking/ftp.service
sudo mv --force --target-directory=/etc/avahi/services/ ftp.service
sudo /etc/init.d/avahi-daemon restart
```

---

### Post by zachtib on 2008-05-20
> **Scheater5 said:**
> Is there any way to tell what the architecture of the install is (x86, amd64) and then pass that on to wget so it downloads the right version?  

run:
```
dpkg-architecture -qDEB_BUILD_ARCH
```

---

### Post by Scheater5 on 2008-05-20
> **zachtib said:**
> run:
```
dpkg-architecture -qDEB_BUILD_ARCH
```

Awesome.  I never knew about that.  Alright, anyone know how to pass that onto wget?

---

### Post by wirelessmonkey on 2008-05-20
For new installs you should include apt-get install build-essential before installing hamachi.

---

### Post by Scheater5 on 2008-05-20
> **wirelessmonkey said:**
> For new installs you should include apt-get install build-essential before installing hamachi.

Good catch.  I've appended it onto the line installing ubuntu-restricted-extras.

As for the architecture thing, I'm betting that one's gonna be tricky.  I think it's gonna take an "if then" kinda thing, along the lines of the test for the user id in the beginning - only I don't fully understand the how that works.  Basically, if someone can't walk me through it, I probably can't do it.

---

### Post by Scheater5 on 2008-05-21
I think I've figured out the architecture/hamachi-gui thing.  Here's the new code.  It works for me, but I don't have a 64 bit system to see what happens.  
> if [&(dpkg-architecture -qDEB_BUILD_ARCH) = i386]; then (wget [http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_i386-hardy.deb);](http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_i386-hardy.deb);) fi

if [&(dpkg-architecture -qDEB_BUILD_ARCH) = amd64]; then (wget [http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_amd64-hardy.deb);](http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_amd64-hardy.deb);) fi

dpkg ./hamachi-gui*

And below, here it is inserted into the whole script

```
# Check if the script is being run as root exit if it is not.
if [ "$UID" -ne "0" ]
then
echo "[ERROR] This script must be run as root"
exit 1
fi
mv /etc/apt/sources.list /etc/apt/sources.list_backup
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse" >> /etc/apt/sources.list
echo "deb http://archive.canonical.com/ubuntu hardy partner" >> /etc/apt/sources.list
mkdir /etc/apt/sources.d
echo "deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main" >> /etc/apt/sources.list.d/sources.list
echo "deb http://packages.medibuntu.org/ hardy free non-free" >> /etc/apt/sources.list.d/sources.list
echo "deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main" >> /etc/apt/sources.list.d/sources.list
apt-get install -y ubuntu-restricted-extras build-essential
wget http://files.hamachi.cc/linux/hamachi-0.9.9.9-20-lnx.tar.gz
tar xfz hamachi-0.9.9.9-20-lnx.tar.gz
cd hamachi-0.9.9.9-20-lnx
make install
./tuncfg/tuncfg
cd ..
cp ./hamachi /usr/bin
hamachi-init
echo "tun" > /etc/modules
if [&(dpkg-architecture -qDEB_BUILD_ARCH) = i386]; then (wget http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_i386-hardy.deb); fi

if [&(dpkg-architecture -qDEB_BUILD_ARCH) = amd64]; then (wget http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_amd64-hardy.deb); fi

dpkg ./hamachi-gui*
apt-get -y install libdvdread3 
/usr/share/doc/libdvdread3/install-css.sh
apt-get install -y install totem-xine
apt-get install -y install libdvdcss2
cd ~
wget http://packages.linuxmint.com/pool/import/s/sunbird/sunbird_0.8-mint1_all.deb
dpkg ./sunbird_0.8-mint1_all.deb
apt-get install thunderbird
apt-get install avant-window-navigator-trunk avant-window-navigator-data-trunk awn-extras-applets-trunk awn-manager-trunk libawn0-trunk python-awn-trunk vala-awn-trunk
apt-get install vsftpd
wget http://www.voxpopulimedia.com/pub/howto/homenetworking/vsftpd.conf
mv -f vsftpd.conf /etc/vsftpd.conf
apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns service-discovery-applet mdns-scan
wget http://www.voxpopulimedia.com/pub/howto/homenetworking/ftp.service
sudo mv --force --target-directory=/etc/avahi/services/ ftp.service
sudo /etc/init.d/avahi-daemon restart
```


hmm...upon a test run, I have gotten something wrong with the if/fi part, because it downloads both no matter what architecture it returns.  Back to the drawing board.

---

### Post by smartboyathome on 2008-05-21
You forgot to put a not section (I am not as familiar with bash, but this is basic programming knowledge for me).

---

### Post by Scheater5 on 2008-05-21
Alright, I understand the logic behind if/then/else statements, but I don't know the syntax in bash (or any programming language, bash is my first "language," if you could call it that).  I'm off to Google!

---

### Post by Scheater5 on 2008-05-22
> if (dpkg-architecture -qDEB_BUILD_ARCH) > i386; then
	(wget [http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_i386-hardy.deb);](http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_i386-hardy.deb);)
else
      echo > /dev/null
fi

if (dpkg-architecture -qDEB_BUILD_ARCH&#8221; > amd64); then
	(wget [http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_amd64-hardy.deb](http://downloads.sourceforge.net/hamachi-gui/hamachi-gui_0.9.5-0_amd64-hardy.deb))
else
	echo > /dev/null
fi



Here's what I got so far.  I know there's a fault with the first if statement.  I don't know how to test to see if an output is or is not a given statement.  "command - output, is output = given statement"  I thought I understood from some scripts I saw (which, of course, I can't find) that > would do that, but now it seems that, obviously enough, tests to see if it is greater than or not.  Basically, what I need is "if 'command output' is a, then command1; if 'command output' is b, then command2"

---

