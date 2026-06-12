---
title: "Setting up a fully functional Media server with 14.04 LTS"
date: 2014-04-25
forum: Security
---

### Post by Cyndre on 2014-04-25
**Purpose**
To set up a secured (mostly) open-source server that can act as a data hub, wireless router with firewall, TOR node, and delegate printing to two laser printers (one color, other black). Rolling in a LAMP server is not needed, already bought some off-site hosting. This machine is for internal network use, holding down a VPN where I can access (with proper authentication) SSH and VNC, plus CUPS over Samba. I want this to replace using a commercial router, already bought a PCIe wireless N card that can use master mode and has open source drivers. Once it is running, I will be putting in a managed switch with hardware firewall between it and the modem, and the only other thing connected at that level would be IP cameras and a Raspberry Pi for managing coin mining and other fun stuff.

**Procedure**
I have put together the box using a dual core AMD with rather simple motherboard (only 2 memory slots, 2GB total) and a couple large hard drives that were laying around. The PCIe wireless card is from [ThinkPenguin]("https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-pcie-card-gnu-linux-v4-tpe-n300pcie4"), got the 3 year warranty as well so I will be contacting them for help too (this thread will chronicle the whole process) and also trying to contact the [WebUpd8 Developers]("http://ppa.webupd8.org/post/76219000363/ap-hotspot-0-3-1-released") about their script as well. I have set up and troubleshooted existing large network systems that had all of these individual components, but this is my first time getting it going all together. After getting it running, I want to publish a proper tutorial with links out to all the research I did on the way.

**Results**
I started planning this out with 13.10, got to the point of having most everything (really too much overall) installed and 14.04 LTS was coming out, so I have started from scratch today in setting it up again. I used my notes from 13.10 (which I have set up many times) and added in extras for usability and broad compatibility. The issue I got stuck on in 13.10 was dnsmasq conflicting with dhcpd, so ap-hotspot would configure and start but not give out IPs to any clients, so connections would time out. Then I installed [Hamaguichi]("https://launchpad.net/~webupd8team/+archive/haguichi") in order to have somewhat secure and simple access to the machine while I was at other locations, but in the process of trying to set up TightVNC I borked the whole thing and LightDM would no longer login. So, I set up 14.04, after dealing with one of my initial issues of not being able to boot from USB on this mobo and not having any blank DVDs around to burn the new disk image to. The solution was in [Plop Boot Manager]("http://www.plop.at/en/bootmanager/plpbt.bin.html#rungrub2"), and I re-added it again after getting 14.04 installed just for future-proofing. The printers are actually needing a physical overhaul (got a refurb kit for one, the other needs some duct tape after a cleaning) but I got their software worked out enough to print once before, so I expect it to happen again with [HPLIP over Parallel]("http://hplipopensource.com/node/217") (HP LaserJet 8000) and [Foo2zjs over USB]("http://foo2zjs.rkkda.com/") (Konica Minolta QMS 2300 DL). I set up simple samba sharing through the GUI, and CUPS is installed alright. Set up GUFW as a basic software firewall, I am not afraid of learning IPtables but have not spent the time to know it well yet. Hamachi seems to work alright for testing purposes anyway, but if I can set up something more secure with/without VPN I am open to that. Being able to print from other devices (google cloud print for starters, but possibly through submitting a file and controlling via VNC). Went with RealVNC server/viewer this time around too, it seems to have better Linux support than TightVNC. This time through dnsmasq seems to be cooperating, but the ap-hotspot script hangs while trying to start. Configures fine, but just stops at "Starting Wireless Hotspot..." which I have to kill, then it tells me if I try it again that "Another process is already running" but trying restart gives "Wireless Hotspot is not active" so I am really at a loss here.

**Questions**
Does anybody have ap-hotspot set up and working in 14.04?
Are there any networking components that are conflicting out of these base installs? I have not configured everything fully yet, did graphical setups but I am sure I have missed config files that might help.
For the media server side of things, how does one set up streaming to any device? Preferably over an ecrypted connection, and not requiring LAMP or too much more software on top of what I already have.
On that note, if there is any software that would be a more lightweight/elegant solution I would love to hear it as well. I have been using Ubuntu full time as my main computers for 5 years now, played around with a bunch of distributions before that and a little bit of larger network administration (mixed, mostly M$ network with Ubuntu Server and CentOS boxes in the background) but there is always more to learn.

Ultimately, the learning process is collective, so I invite others who might be doing this sort of thing to post about their setups and the challenges/failures/feedback faced in getting them going.
I will stick this project through till its humming happily, and I hope that is soon.

[logfiles to come]

---

### Post by Cyndre on 2014-05-04
Okay, so here is a screenshot of ap-hotspot hanging, I ran updates first in hopes of a new version but there were none. I do not know the structure of the script well enough to figure out where it is thowing an error, last time I found out about the dnsmasq/dhcpd problem when I saw that the service was failing to load before the login screen. No such messages this time around.

[IMG]http://i59.tinypic.com/2e1zyvb.png[/IMG]

Edit: Well, waiting has paid off a bit. Via [WebUpd8]("http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html"), I got this part fixed. I guess the hostapd version for 14.04 is buggy, so installing the older version and keeping it from updating let me get the hotspot started, but clients fail to get an IP, like before.
```
cd /tmp
wget [http://archive.ubuntu.com/ubuntu/pool/universe/w/wpa/hostapd_1.0-3ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wpa/hostapd_1.0-3ubuntu2.1_i386.deb)
sudo dpkg -i hostapd*.deb
sudo apt-mark hold hostapd
```
Wondering if there is some configuration I am missing with dnsmasq or dhcpd, so that it all plays together nicely. I want dhcpd to keep working with nm-applet to manage the outbound connection, and dnsmasq to hand out IPs for wireless clients. Any ideas?

[IMG]http://i61.tinypic.com/1pgtnm.png[/IMG]

The Sessions still open message comes up once when first starting it, and the extra ones pop in as I try to connect a wireless client, which hangs on waiting for an IP until timeout, then another Session message pops as the client retries.

---

### Post by Cyndre on 2014-05-05
So, I gave up on trying to pull apart the ap-hotspot script for now, just going with the older version of hostapd and isc-dhcp-server as described [over here]("http://askubuntu.com/questions/180733/how-to-setup-a-wi-fi-hotspot-access-point-mode"). First off, basic setup allowed me to actually connect to the wireless network! But there is no outbound connection, it was not bridging properly. I realized the command of "echo 1 > /proc/sys/net/ipv4/ip_forward" was not actually working, so I dug around in /etc/sysctl.conf and found the setting there ([COLOR=#000000]net.ipv4.ip_forward = 1)[/COLOR]. Going down for a reboot now...

Edit: Alternate way to set that value is with [COLOR=#222225]sudo sysctl net.ipv4.ip_forward=1
I have not been able to get it to work still, not sure if I should try with dnsmasq again now that hostapd is working properly...[/COLOR]

---

### Post by Cyndre on 2014-05-07
Started a thread over at [askubuntu]("https://askubuntu.com/questions/462534/getting-wifi-ap-working-with-hostapd-and-isc-dhcp-server-xubuntu-14-04") for the wireless issue.
Here is my install log so far...

```
Install with proprietary codecs & updates
Partition 1: ext4, 20gb, mount as /
Partition 2: ext4, remaining space, mount as /home
Require password to login, encrypt home folder

sudo add-apt-repository -y ppa:nilarimogard/webupd8
sudo add-apt-repository -y ppa:webupd8team/tor-browser
sudo add-apt-repository -y ppa:webupd8team/haguichi
sudo add-apt-repository -y ppa:kilian/f.lux
sudo add-apt-repository -y ppa:otto-kesselgulasch/gimp
sudo add-apt-repository -y ppa:videolan/stable-daily

sudo apt-get install synaptic aptitude gdebi gksu wget leafpad linux-firmware-nonfree
sudo aptitude update && sudo aptitude full-upgrade
sudo aptitude install haguichi tor-browser fluxgui bridge-utils tasksel todo-indicator fslint gufw keepassx audacious audacity youtube-dl youtube-dlg vlc gxine mencoder mpeg2dec vorbis-tools id3v2 mpg321 mpg123 libflac++6 totem-mozilla icedax tagtool easytag id3tool lame libmad0 libjpeg-progs flac faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1 mpeg3-utils mpegdemux liba52-0.7.4-dev libquicktime2 libav-tools libavcodec-extra build-essential checkinstall cdbs devscripts dh-make fakeroot libxml-parser-perl check pdfmod mupdf-tools unace rar unrar p7zip-rar p7zip zip unzip sharutils uudeview mpack arj cabextract file-roller samba smbc system-config-samba winbind cifs-utils filezilla filezilla-common curl deluge-torrent xfce4-goodies xubuntu-restricted-extras xubuntu-restricted-addons xfce4 xfwm4-themes tango-icon-theme shiki-colors-xfwm-theme secure-delete xarchiver audacious brasero clamav clamav-unofficial-sigs clamtk bleachbit cloudprint cups-pdf geany geany-plugins gimp gimp-gmic gimp-data-extras gimp-gutenprint gimp-plugin-registry gparted gtk2-engines-xfce gtk3-engines-xfce libreoffice libreoffice-math libreoffice-pdfimport xpdf

sudo chmod u+s /usr/sbin/hddtemp

sudo tasksel
#OpenSSH server
#DNS server
#fonts

#gufw
sudo ufw allow 22
sudo ufw allow 67,68/udp
sudo ufw deny 5353/udp
sudo ufw deny 5900/tcp
sudo ufw deny 25/tcp
sudo ufw deny 135,139,445/tcp
sudo ufw deny 137,138/udp
sudo ufw deny 110
sudo ufw deny 2049
sudo ufw deny 143
sudo ufw deny 21/tcp
sudo ufw enable

sudo apt-get install --assume-yes avahi-utils libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg-dev libsnmp-dev libtool libusb-1.0.0-dev wget python-imaging policykit-1 policykit-1-gnome gtk2-engines-pixbuf python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify2 python python-reportlab libsane libsane-dev sane-utils xsane
cd Downloads
tar xvfz hplip-3.14.4.tar.gz
cd hplip-3.14.4/
./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --disable-libusb01_build --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-udev_sysfs_rules --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build --enable-pp-build
make
sudo make install
sudo usermod -a -G lp $USER
cd ..
tar xvfz foo2zjs.tar.gz
cd foo2zjs/
make
./getweb 2300
./getweb 2430
sudo make install
sudo make cups


sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

unzip plpbt-5.0.14.zip
cd plpbt-5.0.14
sudo cp plpbt.bin /boot
sudo nano /etc/grub.d/40_custom

menuentry "Plop Boot Manager" {
    set root=(hd0,1)
    linux16 /boot/plpbt.bin
}


sudo nano /etc/default/grub

#GRUB_HIDDEN_TIMEOUT=0

sudo update-grub
sudo update-grub2


sudo nano /etc/sysctl.conf

# Decrease swap usage to a reasonable level
vm.swappiness=10
# Improve cache management
vm.vfs_cache_pressure=50


sudo nano /etc/default/keyboard

XKBOPTIONS="terminate:ctrl_alt_bksp"


#Cleaning Up
sudo apt-get -f install && sudo apt-get autoremove && sudo apt-get -y autoclean && sudo apt-get -y clean

```

---

### Post by Cyndre on 2014-05-25
So at least have one good reason for this server to be running now, got CUPS configured well enough to be shared over the local network and google cloud print service. All after doing a complete refurb on the printer of course, it still jams sometimes but is working rather well. The biggest hitch left is that PDFs printed via google seem to cause memory issues in the LaserJet. The job gets to "Processing" forever, cancelling the job in CUPS and HPLIP leaves it unable to print until I reboot the printer and sometimes the computer too. Currently devising a way to have a dropbox on the computer with an associated cron job to regularly print whatever files are new.

To simplify things, I disabled all my firewall profiles while setting this up, then going to re-enable afterwards with exceptions for each service.

In the CUPS web interface, I have the boxes for "Share printers" and "Allow remote administration checked. In the conf file, these are the changes I made:
```
BrowseAllow @LOCAL    BrowseLocalProtocols dnssd
    DefaultEncryption IfRequested
    <Location [all]>
    Allow @LOCAL
    </Location>
```
I tried using the cloudprint package from google, which is the same as the [script from armoo]("https://github.com/armooo/cloudprint/issues/52"). It did not work, I could log in but then it would give an error while running,"ERROR: Could not Connect to Cloud Service. Will Try again in 60 Seconds." never actually making a successful connection to the internet.
After that, I tried using the [excellent instructions from Jeff Rebeiro]("http://blog.rebeiro.net/2012/12/google-cloud-print-daemon-for-ubuntu.html") for setting up a cloudprintproxy service, based off of the google instructions for [running cloud printers on linux servers]("http://support.google.com/cloudprint/answer/2906017?hl=en"). It still would not work, this time not even getting an instance of the program running, even though service commands would act like it was responding properly. At this point though, I could see how to do it directly, without his script, and installed chromium as a dedicated google apps platform (to keep it separate from the main google chrome browser, in case the apps had to be restarted). After getting chromium set up through the Advanced Options dialog for adding a printer, cloud print worked! So I set up an autostart service, basically the same thing as done with Rebeiro's script, but without using a partial & script-generated profile. linux support from google is doing some good, but their solutions have very little to be said about them, and it is often up to the users to figure out all of what is going on. Case in point, the command line switches for chrome/chromium are not fully documented, because they may disappear at a whim if they are not main features. Luckily there are some [badass users who are better at documentation]("http://peter.sh/experiments/chromium-command-line-switches/") than google.

So my solution ended up looking like this in the application autostart section of system startup:
```
Name: Chromium Cloud Print Service
    Description: Chromium Print Daemon Service
    Command: /usr/lib/chromium-browser/chromium-browser --type=service --enable-cloud-print-proxy --no-service-autorun --noerrdialogs
```
Up next is to make cron jobs for the drop folder, and to restart the chromium service once daily, to refresh the connection.
Also getting a [Tor Relay]("https://www.torproject.org/docs/tor-relay-debian.html.en") running, and [VNC]("https://help.ubuntu.com/community/VNC") to be able to remotely administer it. Looking at different possibilities from Hamachi for VPN, it was what I used in Windows but would prefer something more open. Until then, I will just use VNC tunneled over SSH.

---

