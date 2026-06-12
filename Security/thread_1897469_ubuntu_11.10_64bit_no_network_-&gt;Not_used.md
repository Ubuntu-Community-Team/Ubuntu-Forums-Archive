---
title: "ubuntu 11.10 64bit no network -&gt;Not used"
date: 2011-12-19
forum: Security
---

### Post by oklokl on 2011-12-19
[http://cafe.naver.com/linuxcare/41715](http://cafe.naver.com/linuxcare/41715)
all ucc

[http://youtu.be/6uI5DzlDEgw](http://youtu.be/6uI5DzlDEgw)
my pc..

[http://youtu.be/zu-pK4lNYFE](http://youtu.be/zu-pK4lNYFE)
iptraf

[http://youtu.be/l5j8KEcIsCM](http://youtu.be/l5j8KEcIsCM)
iptraf 2

Do not use the Internet
No samba ->remove
No mysql ->remove
No p2p.. -> No start
No update 
.. what.. 
Using the Internet? Someone is using?

hacking?

sudo lsof -n -i -P
sudo netstat -tulnp

Please help me..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209358&stc=1&d=1324306081[/IMG]

[http://cafe.daum.net/candan/HgwY/57](http://cafe.daum.net/candan/HgwY/57)
my system

Firewall
gufw
fail2ban 
iplist 

Reinstall the
Is the same
gfuw..
If an Internet connection
ufw setting
sudo ufw deny in to any
sudo ufw allow out 53,68,137,138/udp
sudo ufw allow out 20,21,22,80,139,443/tcp
sudo ufw deny out to any

---

### Post by Paddy Landau on 2011-12-19
I do not quite understand your question.

Are you asking how to completely disable Internet access?

Click your network icon at the top right of your screen. Clear both check-marks next to *Enable Networking* and *Enable Wireless* (see attached screen-shot).

You don't need to do any of the other stuff.

---

### Post by oklokl on 2011-12-19
Are you asking how to completely disable Internet access?
my pc-> other unauthorized use.
Illegal Connections -> want blocked.
Wireless is not ...
Answer Thank you.

&#51064;&#53552;&#45367; &#50672;&#44208;&#51012; &#54616;&#47732;.. &#50508;&#49688; &#50630;&#45716; &#50672;&#44208;&#51012; &#54616;&#45348;&#50836;.. &#44536;&#47000;&#49436; &#44536;&#47111;&#49845;&#45768;&#45796;..
&#51228; &#51064;&#53552;&#45367;&#51004;&#47196; &#47676;&#44032;&#47484; &#45796;&#50868;&#48155;&#44144;&#45208; &#49569;&#49905; &#54616;&#45716; &#44163; &#44057;&#49845;&#45768;&#45796;.. &#44536;&#47000;&#49436; &#55192;&#46300;&#45348;&#50836;..
&#50612;&#46523;&#44172; &#54644;&#44208;&#51060; &#50504;&#46112;&#44620;&#50836;?..
&#45796;&#47480; &#51064;&#53552;&#45367;&#51008; &#54616;&#51648; &#50506;&#44256; &#51080;&#45716; &#49345;&#53468;&#51077;&#45768;&#45796;..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209398&stc=1&d=1324348114[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209400&stc=1&d=1324348343[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209402&stc=1&d=1324348892[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209401&stc=1&d=1324348892[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209404&stc=1&d=1324353410[/IMG]

---

### Post by Paddy Landau on 2011-12-20
I'm sorry, we seem to have a language problem here.

I am still not quite sure what you want.

Do you want a firewall?

Or do you want to allow network access, but no other Internet connection?

Or something else?

---

### Post by oklokl on 2011-12-20
Unknown connection
 non-ip access (I did not remote network create <- Process)
My pc .. Incoming <- Attack  <-  Process(hiddn Unknown)
Find a cause
Do not want -> unlawfulness access
The safe use ->pc ubuntn..
 I want

&#51228;&#44032; &#50896;&#54616;&#51648; &#50506;&#45716; &#50529;&#49468;&#49828; &#50672;&#44208;&#51060; &#46308;&#50612; &#50741;&#45768;&#45796;..
&#50896;&#51064;&#51012; &#52286;&#44256; &#51080;&#49845;&#45768;&#45796;.. &#12640;&#12640;

reinstall format
 Is the same

---

### Post by emiller12345 on 2011-12-21
Not sure if I understand what they are talking about, but I'm wondering if they are concerned about the DHCP client service that is running... UDP port 68
To disable the dhclient you'll need to also disable NetworkManager
```
sudo service network-manager stop
```
To start it back up again...
```
sudo service network-manager start
```

---

### Post by oklokl on 2011-12-21
thanks but.. 
gnome-nettool -> my ip port view..
Random open port.. ->my pc..
Random port non-ip ->Hidden open.. ->Unexplained -> unknown connection

Ip 68 trust  -> [http://www.kt.com/](http://www.kt.com/) 
korean network ->Internet Service Provider
[http://blog.naver.com/skjtry/20007298955](http://blog.naver.com/skjtry/20007298955)

My worries -> Hidden -> Incoming <- Attack
Suspicious behavior

sudo service network-manager stop
Incoming ->Move - No change

---

### Post by Paddy Landau on 2011-12-21
> **oklokl said:**
> My worries -> Hidden -> Incoming <- Attack
Suspicious behavior
How do you know that there is suspicious behaviour?
Can you tell us what you see that makes you think you have suspicious behaviour?

---

### Post by oklokl on 2011-12-21
thanks
samba not open.. ->access  -> Does not constitute
I do not use services ->no make
I do not configure services

 ufw nmp china ->Service ->Activated force

[COLOR=#FF0000]avahi-daemon ->[/COLOR]access

or Born unknown services ->make..
Evidence
So has been cleared
[COLOR=#FF0000]sudo apt-get autoremove avahi-daemon -y
[/COLOR][COLOR=#FF0000]sudo apt-get autoremove cups -y[/COLOR]
[COLOR=#FF0000]sudo apt-get autoremove cups-client -y[/COLOR]
[COLOR=#FF0000]sudo apt-get autoremove cups-common -y
[/COLOR][COLOR=#FF0000]sudo apt-get autoremove telnet -y[/COLOR]
[COLOR=#FF0000]sudo apt-get autoremove openssh-client -y[/COLOR]
[COLOR=#FF0000]sudo apt-get autoremove samba-common -y
my setting system.. T..T
iplist [/COLOR]
   Check
china ip access->1433, 6000 port 8080 
But until then unknown phenomenon

[http://youtu.be/6uI5DzlDEgw](http://youtu.be/6uI5DzlDEgw)
my pc..
Does not work
 Traffic Users
I suspect this is 

[http://youtu.be/zu-pK4lNYFE](http://youtu.be/zu-pK4lNYFE)
iptraf

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209484&stc=1&d=1324465205[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209486&stc=1&d=1324465384[/IMG]

System Settings. [http://cafe.daum.net/candan/HgwY/57](http://cafe.daum.net/candan/HgwY/57)

---

### Post by spynappels on 2011-12-21
That just looks like automated MSSQL port attacks, which are being blocked anyway, more annoying than suspicious to me...

---

### Post by oklokl on 2011-12-21
Penetration
 Allow illegal
 Someone can open my computer.
 Attack scenarios -> Success T..T
Unseen attacks the root

---

### Post by Paddy Landau on 2011-12-21
> **oklokl said:**
> Someone can open my computer.
How do you know this?

The YouTube video showed downloading, not uploading.
Perhaps it is your Update Manager? Updating your computer?

Do you have Ubuntu Desktop or Ubuntu Server?

---

### Post by spynappels on 2011-12-21
> **Paddy Landau said:**
> How do you know this?

The YouTube video showed downloading, not uploading.
Perhaps it is your Update Manager? Updating your computer?

Do you have Ubuntu Desktop or Ubuntu Server?

Agreed with Paddy, only download traffic seen. Also, the only unrecognised thing in the processes list is the terminal sh script in do_wait mode. What is that?

---

### Post by oklokl on 2011-12-21
The YouTube video showed downloading, not uploading.
Perhaps it is your Update Manager? Updating your computer?

Not Download
Not Update..
..
Not Ubuntu Server?
I do not use any state
My computer does not know the traffic is increased with
Is not known to be a cause

Agreed with Paddy, only download traffic seen. Also, the only  unrecognised thing in the processes list is the terminal sh script in  do_wait mode. What is that?
I would like to give my computer show.
 Tell me Do you have instructions that can show the process?
pstree
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9516;&#9472;dhclient
     &#9474;                &#9492;&#9472;2*[{NetworkManager}]
     &#9500;&#9472;accounts-daemon&#9472;&#9472;&#9472;{accounts-daemo}
     &#9500;&#9472;acpid
     &#9500;&#9472;anacron&#9472;&#9472;&#9472;sh&#9472;&#9472;&#9472;run-parts&#9472;&#9472;&#9472;apt&#9472;&#9472;&#9472;sleep
     &#9500;&#9472;atd
     &#9500;&#9472;bamfdaemon&#9472;&#9472;&#9472;{bamfdaemon}
     &#9500;&#9472;colord&#9472;&#9472;&#9472;2*[{colord}]
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;64*[{console-kit-da}]
     &#9500;&#9472;cron
     &#9500;&#9472;3*[dbus-daemon]
     &#9500;&#9472;2*[dbus-launch]
     &#9500;&#9472;dconf-service&#9472;&#9472;&#9472;2*[{dconf-*********]
     &#9500;&#9472;fail2ban-server&#9472;&#9472;&#9472;24*[{fail2ban-serve}]
     &#9500;&#9472;freshclam
     &#9500;&#9472;gam_server
     &#9500;&#9472;2*[gconfd-2]
     &#9500;&#9472;geoclue-master
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gksu&#9472;&#9472;&#9472;sudo&#9472;&#9472;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                              &#9500;&#9472;gnome-pty-helpe
     &#9474;                              &#9492;&#9472;3*[{gnome-terminal}]
     &#9500;&#9472;gnome-keyring-d&#9472;&#9472;&#9472;4*[{gnome-keyring-}]
     &#9500;&#9472;gnome-screensav&#9472;&#9472;&#9472;2*[{gnome-screensa}]
     &#9500;&#9472;gvfs-afc-volume&#9472;&#9472;&#9472;{gvfs-afc-volum}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daem}]
     &#9500;&#9472;gvfs-gdu-volume
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-metadata
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;indicator-appli&#9472;&#9472;&#9472;{indicator-appl}
     &#9500;&#9472;indicator-datet&#9472;&#9472;&#9472;2*[{indicator-date}]
     &#9500;&#9472;indicator-messa&#9472;&#9472;&#9472;{indicator-mess}
     &#9500;&#9472;indicator-sessi&#9472;&#9472;&#9472;2*[{indicator-sess}]
     &#9500;&#9472;indicator-sound&#9472;&#9472;&#9472;2*[{indicator-soun}]
     &#9500;&#9472;iplist&#9472;&#9472;&#9472;3*[{iplist}]
     &#9500;&#9472;lightdm&#9472;&#9516;&#9472;Xorg
     &#9474;         &#9500;&#9472;gnome-session&#9472;&#9516;&#9472;compiz&#9472;&#9516;&#9472;sh&#9472;&#9472;&#9472;unity-window-de
     &#9474;         &#9474;               &#9474;        &#9492;&#9472;2*[{compiz}]
     &#9474;         &#9474;               &#9500;&#9472;ejecter&#9472;&#9472;&#9472;{ejecter}
     &#9474;         &#9474;               &#9500;&#9472;gdu-notificatio
     &#9474;         &#9474;               &#9500;&#9472;glipper&#9472;&#9472;&#9472;{glipper}
     &#9474;         &#9474;               &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;3*[{gnome-settings}]
     &#9474;         &#9474;               &#9500;&#9472;nabi
     &#9474;         &#9474;               &#9500;&#9472;nautilus&#9472;&#9472;&#9472;2*[{nautilus}]
     &#9474;         &#9474;               &#9500;&#9472;nm-applet&#9472;&#9472;&#9472;{nm-applet}
     &#9474;         &#9474;               &#9500;&#9472;polkit-gnome-au&#9472;&#9472;&#9472;{polkit-gnome-a}
     &#9474;         &#9474;               &#9500;&#9472;sudo&#9472;&#9472;&#9472;ipblock&#9472;&#9472;&#9472;java&#9472;&#9472;&#9472;18*[{java}]
     &#9474;         &#9474;               &#9500;&#9472;zeitgeist-datah&#9472;&#9472;&#9472;{zeitgeist-data}
     &#9474;         &#9474;               &#9492;&#9472;3*[{gnome-session}]
     &#9474;         &#9492;&#9472;2*[{lightdm}]
     &#9500;&#9472;modem-manager
     &#9500;&#9472;notify-osd&#9472;&#9472;&#9472;2*[{notify-osd}]
     &#9500;&#9472;polkitd&#9472;&#9472;&#9472;{polkitd}
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9500;&#9472;rsyslogd&#9472;&#9472;&#9472;3*[{rsyslogd}]
     &#9500;&#9472;rtkit-daemon&#9472;&#9472;&#9472;2*[{rtkit-daemon}]
     &#9500;&#9472;snort
     &#9500;&#9472;udevd&#9472;&#9472;&#9472;2*[udevd]
     &#9500;&#9472;udisks-daemon&#9472;&#9516;&#9472;udisks-daemon
     &#9474;               &#9492;&#9472;2*[{udisks-daemon}]
     &#9500;&#9472;unity-applicati&#9472;&#9472;&#9472;2*[{unity-applicat}]
     &#9500;&#9472;unity-files-dae&#9472;&#9472;&#9472;{unity-files-da}
     &#9500;&#9472;unity-music-dae&#9472;&#9472;&#9472;{unity-music-da}
     &#9500;&#9472;unity-musicstor&#9472;&#9472;&#9472;{unity-musicsto}
     &#9500;&#9472;unity-panel-ser&#9472;&#9472;&#9472;2*[{unity-panel-se}]
     &#9500;&#9472;upowerd&#9472;&#9472;&#9472;2*[{upowerd}]
     &#9500;&#9472;upstart-socket-
     &#9500;&#9472;upstart-udev-br
     &#9492;&#9472;zeitgeist-daemo&#9472;&#9516;&#9472;cat
                       &#9492;&#9472;{zeitgeist-daem}

---

### Post by emiller12345 on 2011-12-21
> **spynappels said:**
> That just looks like automated MSSQL port attacks, which are being blocked anyway, more annoying than suspicious to me...
+1 automated port scan for MSSQL
If you want, you could add a NAT'd router in front of your computer. This will add one more layer of defense, and you won't be bombarded with all of these port scanning attempts.  You'd have much more of a problem if you were running MSSQL which I'm assuming your not.

---

### Post by oklokl on 2011-12-21
thanks.. but.. sorry
Please review the full article, once again
I do not think any problem is in mysql
Are usually aware of the attack
Remove mysql

Unknown traffic
 Attempts to access
non-ip..

---

### Post by emiller12345 on 2011-12-21
I'm not sure you had the correct command for uninstalling all of those packages earlier 
( [COLOR=#FF0000]sudo apt-get autoremove avahi-daemon -y[/COLOR] ) to chek...
```
$ dpkg-query -s avahi-daemon | grep "^Status"
```
a response like
```
Status: install ok installed
```
means it's still installed, and
```
Status: unknown ok not-installed
```
means its not installed.

I usually use [COLOR=#FF0000]sudo apt-get purge avahi-daemon -y[/COLOR]

---

### Post by oklokl on 2011-12-21
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209532&stc=1&d=1324528091[/IMG]
root@ubuntu:/home/ubuntu# dpkg-query -s avahi-daemon | grep "^Status"
`avahi-daemon' &#54056;&#53412;&#51648;&#45716; &#49444;&#52824;&#54616;&#51648; &#50506;&#50520;&#51004;&#47728; &#51221;&#48372;&#46020; &#50630;&#49845;&#45768;&#45796;.
&#50500;&#52852;&#51060;&#48652; &#54028;&#51068; &#51221;&#48372;&#47484; &#48372;&#47140;&#47732; dpkg --info&#47484; &#49892;&#54665;&#54616;&#49884;&#44256; (= dpkg-deb --info)
&#50500;&#52852;&#51060;&#48652; &#45236;&#50857;&#51012; &#48372;&#47140;&#47732; dpkg --contents&#47484; &#49892;&#54665;&#54616;&#49901;&#49884;&#50724; (= dpkg-deb --contents)
root@ubuntu:/home/ubuntu# 

Status: unknown ok not-installed ->Message
No information
thanks

---

