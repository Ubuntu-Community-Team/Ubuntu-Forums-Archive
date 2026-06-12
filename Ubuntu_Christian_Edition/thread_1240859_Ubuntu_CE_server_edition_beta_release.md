---
title: "Ubuntu CE server edition beta release"
date: 2009-08-15
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-08-15
As there are feedback about the need of church management software, I decided to create server edition. This server edition is also a live cd !! As I would expect a small church would not have much resources, this server edition is ALL-IN-ONE edition i.e. you would be able to do:

- Church administration
- Web hosting ready
- Desktop ready.

Below are the software included in this release:

1. Churchinfo
ChurchInfo is a free church database program to help churches track members, families, groups, pledges and payments. Our feature set is comparable to expensive church management software packages.  Our users are supported by an open-source community of people who volunteer their time and energy to make this technology available to all churches.
[http://www.churchdb.org/](http://www.churchdb.org/)

2. Church Website in a Box
The 'Church Website in a Box' is a MySQL/PHP content management system designed to be easily deployed and used by any church. All content management and configuration can be done using a web browser. It is an integration of many other projects.
[http://sourceforge.net/projects/churchwebsite/](http://sourceforge.net/projects/churchwebsite/)

3. Prayer Board
Records, organizes, and displays requests for prayer. Users access the program via their web browser.
[http://sourceforge.net/projects/phpprayerboard/](http://sourceforge.net/projects/phpprayerboard/)

On top of those 3 software, I also include packages from ubuntu ce desktop version, minus gnucash (would also be removed from desktop version):


1. dansguardian gui (complete with dansguardian, tinyproxy and firehol, all are enabled by default)

2. xiphos (I think it is the best bible in linux so far)
Xiphos (formerly known as GnomeSword) is a Bible study tool written for Linux, UNIX, and Windows under the GNOME toolkit, offering a rich and featureful environment for reading, study, and research using modules from The SWORD Project and elsewhere. It is open-source software, and available free-of-charge to all.
[http://xiphos.org/](http://xiphos.org/)

3. OpenSong:
OpenSong is a free, open-source software application created to manage lyrics, chords, lead sheets, overheads, computer projection, and more.
[http://www.opensong.org/](http://www.opensong.org/)

4. e-sword installer : to bring e-sword (one of the best bible software) to linux easily.
e-Sword is a fast and effective way to study the Bible. e-Sword is feature rich and user friendly with more capabilities than you would expect in a free software package. The fact that e-Sword is free is just one of the blessings and does not speak of the quality of the software. I make my living writing software and I believe I have put forth my best effort in this endeavor. The real work, however, was put in by the godly men and women who devoted countless years creating the texts that have been made available for our benefit.
[http://www.e-sword.net/](http://www.e-sword.net/)

5. wine (latest release)
To facilitate people converting from Microsoft Windows to linux.
[http://www.winehq.org/](http://www.winehq.org/)

6. encfs-gui (encryption directory management)
Easily create, and manage encrypted directory.
EncFS provides an encrypted filesystem in user-space. It runs without any special permissions and uses the FUSE library and Linux kernel module to provide the filesystem interface. EncFS is open source software, licensed under the GPL.

As with most encrypted filesystems, Encfs is meant to provide security against off-line attacks; ie your notebook or backups fall into the wrong hands, etc.
[http://www.arg0.net/encfs](http://www.arg0.net/encfs)

7. linbread
Daily bible verse, launch at login, one verse per day.

8. Bible trivia
Daily question and answer about bible facts, one question per day.

Known issue:
1. There is no sound alert when the greeter is ready
2. Login and logout sound is hardcoded, you would not be able to change or disable it (easily).

Download link:

[http://www.livingtorrents.com/torrents-details.php?id=685](http://www.livingtorrents.com/torrents-details.php?id=685)

---

### Post by david_kt on 2009-08-15
Below are some important information in order to use ubuntu ce server edition:


Churchinfo (application > internet > churchinfo ) :
username: Admin
password: churchinfoadmin

Church in a box ([http://localhost](http://localhost)) :
username:admin
password:admin

PhpMyAdmin ([http://localhost/phpmyadmin](http://localhost/phpmyadmin) )
username: root
Password:root

Editing prayer board ([http://localhost/prayerboard](http://localhost/prayerboard)) :

```
gksudo gedit /var/www/prayerboard/prayerboard_cfg.php
```



mysql:
username: root
password: root

Below is instruction to change mysql root password. I will try to make a script to make it easier. In the mean time, please carefully follow below steps if you want ot change mysql password:

```
mysqladmin -u root -p'oldpassword' password newpass
```

After that, you have to change churchinfo, Church in a box, and prayer board root password as well:
```

gksudo gedit /var/www/churchinfo/Include/Config.php
```

find //database connection constant

and change:

$sPassword = 'root' 

to

$sPassword = 'newpass' 

```
gksudo gedit /var/www/prayerboard/prayerboard_cfg.php
```

Find // setup your MySql database here

and change:

$cfg['mysql_password'] =  'root'

to

$cfg['mysql_password'] =  'newpass'

For Church Website in a box, there is a little difficult.:

_Main site_
Go to this site:
[http://www.tools4noobs.com/online_php_functions/base64_encode/](http://www.tools4noobs.com/online_php_functions/base64_encode/)
Key in your new password to encode and click based 64 encode.
Let's say the output is 'encoded newpass'

OR, you could install php5-cli

```
sudo apt-get install php5-cli
```

and then encode your new password:
```

php -r 'echo base64_encode($argv[1]);' newpass && echo
```

The output would be the same as above 'encoded newpass'

After that,


```
gksudo gedit /var/www/config.php
```

Find $pnconfig['dbpass'] = 'cm9vda==';
Change to
$pnconfig['dbpass'] = 'encoded newpass';

_Bulletin Board_

```
gksudo gedit /var/www/modules/phpBB2/config.php
```

find $dbpasswd = "root";

change to
$dbpasswd = "newpass";

DK

---

### Post by oneinch on 2009-08-15
Awesome! I am downloading it now. I am going out of town for the week end but when I get back into town I will install this and give it a try. Good job, keep up the good work.

---

### Post by stlsaint on 2009-08-15
hey i am downloading as we speak...but one question DK...when the final release comes out we wont have to re-install or anything right...i mean we should just be able to upgrade like normal ubuntu? or are there going to be special instructions for us...im asking because i plan on starting to use it right now so just wondering!!

---

### Post by stlsaint on 2009-08-15
i usually have pretty fast internet but for some reason when i try and download this...it runs at 10kb/sec!!! its gonna take me 17hours to download!!!

---

### Post by david_kt on 2009-08-15
Yes, this would be similar to final release, should be easily upgraded.
This server release more or less are final release, unless there is a feedback of serious bug.. I might add one more script to change mysql's root password easily.

I host the file at home, so, may be that is the reason you have slow internet connection. May be you could wait until Jereme upload the iso fle somewhere else.

DK.

---

### Post by david_kt on 2009-08-15
May be some of you experience interupted download as my computer suddenly freeze when I installed S.M.A.R.T. The reason I install it issuddenly 3 of my partition were disconnected. Actually I am able to remount the partition manually, but I thought installing S.M.A.R.T would be good as I would know the hard disk condition.

As I have not completed recovering the harddisk, may be I should give you the link to ubuntu ce server:

[http://www.livingtorrents.com/torrents-details.php?id=679&hit=1](http://www.livingtorrents.com/torrents-details.php?id=679&hit=1)

DK

---

### Post by stlsaint on 2009-08-16
hey maybe that was a good thing DK as i did experience interrupted download at 9 hours left but i started the download on your last posted link and now i will have it in about 1 hours...thanks anyway and thanks for answering post!

---

### Post by stlsaint on 2009-08-16
also is there a specific program that we should be using to check md5sum...please post steps to check.

---

### Post by david_kt on 2009-08-16
> **stlsaint said:**
> also is there a specific program that we should be using to check md5sum...please post steps to check.

That server is belong to Jereme, so you should thank him. At first I tried to host the file at my server as Jereme has not replied my mail yet. But when my computer fail, I guess I have to publish that link. And it is also to test whether or not the file is correct before we publish it to public. The to chek is open terminal and:

md5sum /path/to/ubuntu-9.04-server-christian_edition-i386.iso

If ubuntu-9.04-server-christian_edition-i386.iso is in your home folder, then there is no path needed.

DK

---

### Post by stlsaint on 2009-08-16
nevermind about checksum question...i see it!!!

---

### Post by Viva on 2009-08-16
Great work again. Congrats on the server release:D

---

### Post by david_kt on 2009-09-25
How to change password:

Churchinfo will force you to change the password upon first login.

CWIAB: member list >> edit >> type new password below twice

Prayerboard: No password, just edit it using your normal user (with
sudo) as I have explain in the forum. But you might not need this
prayerboard as the cwiab also have prayer module.

phpmyadmin:
After login, look for "Change password", click it. (under action catogory)

By the way, I found 3 websites using CWIAB:
[http://www.ipcj.org/cwiab/www/](http://www.ipcj.org/cwiab/www/)
[http://www.landisbaptist.com/index.php?theme=LBC-Winter](http://www.landisbaptist.com/index.php?theme=LBC-Winter)
[http://www.cpac.org.nz/index.php?POSTNUKESID=3727ba2f66ac06bed3181d3c22c31fd8](http://www.cpac.org.nz/index.php?POSTNUKESID=3727ba2f66ac06bed3181d3c22c31fd8)

DK

---

### Post by Coglin on 2009-09-29
Thanks for the server release
 
I have installed on a generic PC to act as a proxy server for my network however i have 2 problems thus far
1 - unable to update - can use web browser OK but it can't update vie terminal or gui
2- clients on network - despite setting their proxy to IP:8080 it would sem they are not connecting as i get  time out  in the browser
 
Cheers
Col

---

### Post by david_kt on 2009-09-29
> **Coglin said:**
> Thanks for the server release
 
I have installed on a generic PC to act as a proxy server for my network however i have 2 problems thus far
1 - unable to update - can use web browser OK but it can't update vie terminal or gui
2- clients on network - despite setting their proxy to IP:8080 it would sem they are not connecting as i get  time out  in the browser
 
Cheers
Col

For problem no 1:
There is a proxy setting need to be removed. Below is how to remove it:

Open terminal (Application > Accessories > Terminal)
And run below command:

```
sudo rm /etc/apt/apt.conf.d/01proxy
```

Please see below post as well for other issue:

[http://ubuntuforums.org/showthread.php?t=1274861](http://ubuntuforums.org/showthread.php?t=1274861)

For problem no 2:

There is no proxy setting needed to reach ubuntu ce server. What you have to do is to put the ip address or hostname in the browser, remove the proxy setting.

DK

---

### Post by Coglin on 2009-09-29
Thanks DKT - appreciate the help :KS
 
Apt now sorted :)
 
still can't seem to use CE server as proxy server from another machine :( thanks for the suggestion- i am not trying to get to the CE website - but use Dansguardian setup as my net filter/proxy for LAN PCs
 
BTW - Am also looking to try "net responsibility" to see about reporting on net usage easily - not sure about it tho as looks like it's semi in limbo from forum chatter
 
Chers
Col

---

### Post by david_kt on 2009-09-29
> **Coglin said:**
> Thanks DKT - appreciate the help :KS
 
Apt now sorted :)
 
still can't seem to use CE server as proxy server from another machine :( thanks for the suggestion- i am not trying to get to the CE website - but use Dansguardian setup as my net filter/proxy for LAN PCs

Do you have have two network card? In order to share internet connection, you should have two network card, one connected to internet, one connected to LAN.

DK

---

### Post by Coglin on 2009-09-29
HI DKT
 
Hmmm - no i don't I thought CE ( or dans with squid etc) could do it with just the 1 NIC my previous MS proxy server had just the 1 NIC.
 
My setup is a little cpmplex as i sit inside a Cisco network with 2 layers of switching, an ASA and a VoIP call manager ( thankfully all donated as i work for a NFP)
 
Untangle appliance was using spoofing i think so was blocked by Cisco gear, so thought this might be a solution
 
Thanks
Col

---

### Post by adzik on 2009-09-29
Thanks for all your efforts david_kt. I will be testing this in the next few weeks as my schedule allows. I was about to start piecing together a minimal debian server for Christian org's here, but yours is a much better solution to demo for them, since it seems to be along the lines of what they'll need.
I tell you...sometimes Christian organisations and churches are the most stubborn to change. Thanks again for this server edition. Your work won't go unnoticed.

---

### Post by david_kt on 2009-09-29
> **Coglin said:**
> HI DKT
 
Hmmm - no i don't I thought CE ( or dans with squid etc) could do it with just the 1 NIC my previous MS proxy server had just the 1 NIC.
 
My setup is a little cpmplex as i sit inside a Cisco network with 2 layers of switching, an ASA and a VoIP call manager ( thankfully all donated as i work for a NFP)
 
Untangle appliance was using spoofing i think so was blocked by Cisco gear, so thought this might be a solution
 
Thanks
Col

In that case, you have gateway in your lan which is not the ubuntu ce server and PC on the LAN would able to connect directly to your gateway.

I guess I will still able to set up proxy with that configuration, but you must lock the proxy on the client.

DK

---

### Post by Coglin on 2009-09-29
Thanks DK
 
Appreciate your help on this, sorry for being a little slow - although i have dabbled with Linux for years this is the first time i am trying to impliment in a live work environment
 
I guess i would like confirmation that by using the CE proxy machines IP eg 192.168.0.3:8080 should work as the proxy for clients without having to tweak the CE box to allow then to go through it?
 
Thanks
Col

---

### Post by david_kt on 2009-09-29
> **Coglin said:**
> Thanks DK
 
Appreciate your help on this, sorry for being a little slow - although i have dabbled with Linux for years this is the first time i am trying to impliment in a live work environment
 
I guess i would like confirmation that by using the CE proxy machines IP eg 192.168.0.3:8080 should work as the proxy for clients without having to tweak the CE box to allow then to go through it?
 
Thanks
Col

By default, I block almost all ports, including port 8080. You could try disabling the firewall:

```
sudo /etc/init.d/ubuntu_ce_firewall stop
```

But the firewall would be restarted upon reboot.

DK

---

### Post by Coglin on 2009-09-29
Great - thanks DK - that's sorted it - all i need now is to edit the firewall config to allow 8080 through and all is sweet.
 
I will lock down the proxy settings - use group policy to do it :)

---

### Post by Coglin on 2009-09-30
Hi
 
Was working fine yesterday after disabled firewall, then edited the UKenglish template and now get an error with IP tables not loading properly
 
"iptables v1.4.1.1: -P requires a chain or policy"
 
have googled but not found a likely solution as yet - can't see why this is suddenly happening

---

### Post by david_kt on 2009-09-30
> **Coglin said:**
> Hi
 
Was working fine yesterday after disabled firewall, then edited the UKenglish template and now get an error with IP tables not loading properly
 
"iptables v1.4.1.1: -P requires a chain or policy"
 
have googled but not found a likely solution as yet - can't see why this is suddenly happening

May be you have editted ubuntu_ce_firewall?

But the box should functioning as normal as you do not need iptables. If it do not run properly, you could try:

```
sudo /etc/init.d/ubuntu_ce_firewall stop
```

and see whether or not the box is functioning as normal.

Also please give me the output of:

```
cat /etc/init.d/ubuntu_ce_firewall
``` 

DK

---

### Post by Coglin on 2009-09-30
Thanks David
 
I can use the box as a proxy and it's filteed successfully
 
the box it's self wasn't getting out but now it is
 
DG gui shows redirection off but DG and Tiny both on
 
Great work - looking forward to making it live for users and see what happens:P
 
Would love to have some reporting facility on user activity for future releases and would be willing to help test

---

### Post by david_kt on 2009-09-30
> **Coglin said:**
> 
DG gui shows redirection off but DG and Tiny both on
 
Great work - looking forward to making it live for users and see what happens:P
 
Would love to have some reporting facility on user activity for future releases and would be willing to help test

The redirection is for transparent proxy, it is managed by the firewall. If the firewall off, then the redirection is also off. As a result, you have to set proxy manually for each computers, including the ubuntu ce box, to utilize dansguardian.

As for the log, you could use below command:

```
more /var/log/dansguardian/access.log |grep *DENIED*
```

Or, if you want to save the data on a file:

```
more /var/log/dansguardian/access.log |grep *DENIED* > denied.log
```

Or, if you want to automatically create different file so as no to overrides the old one:

```
more /var/log/dansguardian/access.log |grep *DENIED* > denied_"`date`".log
```

It will append today date and time the name.
It is good to check it from time to time as you would find false positive, and then add those websites to whitelist.

DK

---

### Post by Coglin on 2009-10-01
Thanks David for all your work on UCE and your help specific to my probs :KS

I now have UCE server as my proxy for my 30+ users in the main office. just running on a generic P4 2.6 1Gb RAM and a small HDD PC. :P

Group policy dictates to use it as the proxy when on the LAN and local policy then takes over when not so net access is still possible via users home connections for laptop users.

there are still some tweaks to do tidying up the FW shutdown via a script on login on the CE server so it's automatic and some other housekeeping- but these relate more to my learning to do more within ubuntu not CE specific.

Hope to be able to help others once i know enough myself

May God Bless you

---

### Post by david_kt on 2009-10-01
> **Coglin said:**
> Thanks David for all your work on UCE and your help specific to my probs :KS

I now have UCE server as my proxy for my 30+ users in the main office. just running on a generic P4 2.6 1Gb RAM and a small HDD PC. :P

Group policy dictates to use it as the proxy when on the LAN and local policy then takes over when not so net access is still possible via users home connections for laptop users.

there are still some tweaks to do tidying up the FW shutdown via a script on login on the CE server so it's automatic and some other housekeeping- but these relate more to my learning to do more within ubuntu not CE specific.

Hope to be able to help others once i know enough myself

May God Bless you

To disable firewall, try:

```
sudo update-rc.d -f ubuntu_ce_firewall remove
```

The firewall would not be started on reboot.

DK

---

### Post by Coglin on 2009-10-07
Thanks David
 
Just thought I'd drop a note to say CE server has been our filter/proxy now for almost a week and seems to be behaving. :P
 
the suggested command worked when rerun today after a reboot - Cheers

having fun working through the group Policy to tie things down but still allow access for those with laptops to use their own unfiltered connections at home/on the road
 
Cheers 
Col

---

### Post by Coglin on 2009-11-24
Howdy All
 
Server is running well now for almost 2 months. Filtering approx 30 office staff comfortably using an old P4 2.6 1Gb RAM 30 GB HDD generic PC :D
 
A few legite sites being trapped but adding to white lists proves easy. have not had staff complain about any slowness or other internet issues besides the occasional block.
 
Thanks DKT for all you and your team's work on this

---

### Post by satimis on 2010-03-21
Hi folks,

I have 
ubuntu-9.10-server-christian edition-i386 beta.iso

download on;
[http://www.livingtorrents.com/torrents-details.php?id=685](http://www.livingtorrents.com/torrents-details.php?id=685)

md5sum ubuntu-9.10-server-christian_edition-i386.iso ```

eb36dbff52c06378382304cf190fcd50  ubuntu-9.10-server-christian_edition-i386.iso

```

But Info Hash:	40a67c8bca8dc5c0063c0f9a218486c7a7e13c21

How can I make comparison?  Thanks

B.R.
satimis

---

### Post by david_kt on 2010-03-21
> **satimis said:**
> Hi folks,

I have 
ubuntu-9.10-server-christian edition-i386 beta.iso

download on;
[http://www.livingtorrents.com/torrents-details.php?id=685](http://www.livingtorrents.com/torrents-details.php?id=685)

md5sum ubuntu-9.10-server-christian_edition-i386.iso ```

eb36dbff52c06378382304cf190fcd50  ubuntu-9.10-server-christian_edition-i386.iso

```

But Info Hash:	40a67c8bca8dc5c0063c0f9a218486c7a7e13c21

How can I make comparison?  Thanks

B.R.
satimis

md5sum is correct:

```
eb36dbff52c06378382304cf190fcd50 ubuntu-9.10-server-christian_edition-i386.iso
```

DK

---

### Post by satimis on 2010-03-21
> **david_kt said:**
> md5sum is correct:

```
eb36dbff52c06378382304cf190fcd50 ubuntu-9.10-server-christian_edition-i386.iso
```


Thanks DK

A side question is the bible on "ubuntu-9.10-christian_edition_v6.0-amd64_beta.iso" written in Vietnam language?  I can't read it.  If YES, then how can I replace it with an English bible?

B.R.
satimis

---

### Post by david_kt on 2010-03-21
> **satimis said:**
> Thanks DK

A side question is the bible on "ubuntu-9.10-christian_edition_v6.0-amd64_beta.iso" written in Vietnam language?  I can't read it.  If YES, then how can I replace it with an English bible?

B.R.
satimis

Nope, it is english.

DK

---

### Post by satimis on 2010-03-21
Hi folks,

Now I have the server edition installed running on a VM of VirtualBox.  Please advise the name of user and password to login ChurchInfo.  Thanks

B.R.
satimis

---

### Post by stlsaint on 2010-03-21
I think it is username:admin/password: churchinfo
which you will need to change at first login.

---

### Post by satimis on 2010-03-21
> **stlsaint said:**
> I think it is username:admin/password: churchinfo
which you will need to change at first login.

Tried following combination;
user: admin
password: pass/passwd/password

none of them can work.

According to its website;
[http://www.churchdb.org/](http://www.churchdb.org/)

user: admin
password: demoadmin

Also can't work

satimis

---

### Post by david_kt on 2010-03-21
> **satimis said:**
> Tried following combination;
user: admin
password: pass/passwd/password

none of them can work.

According to its website;
[http://www.churchdb.org/](http://www.churchdb.org/)

user: admin
password: demoadmin

Also can't work

satimis

Please read the second post of this thread carefully (on the first page), it is available there.

DK

---

### Post by satimis on 2010-03-22
> **david_kt said:**
> Nope, it is english.




Hi DK,

On;
Applications -> Wine -> Program -> Bible Verse -> Bible Verse

only a vertical bar of about 20mm(width)x100mm(height) starts with codes on it.  How to fix this problem?  To uninstall it?  TIA

B.R.
satimis

---

### Post by Coglin on 2010-04-27
HI DKT & Team
 
I am looking to run UCE server in a 64 bit hyper V environment ( i have a spare CPU core and RAM on that box) and ditch the old P4 PC.
 
from a look at the download page the server is only available in a 32 bit beta version - is this correct?
 
if so any plans for a 64 bit version?

---

### Post by david_kt on 2010-04-27
> **Coglin said:**
> HI DKT & Team
 
I am looking to run UCE server in a 64 bit hyper V environment ( i have a spare CPU core and RAM on that box) and ditch the old P4 PC.
 
from a look at the download page the server is only available in a 32 bit beta version - is this correct?
 
if so any plans for a 64 bit version?

Yes we do not have 64 bit version for server yet. I will consider to built 64 bit for next version.

DK

---

### Post by Coglin on 2010-04-27
Thanks David
 
Is your Server still a beta version or it has been honed and is a full "release" version now?

---

### Post by david_kt on 2010-04-27
> **Coglin said:**
> Thanks David
 
Is your Server still a beta version or it has been honed and is a full "release" version now?

Actually there is not much difference between beta and full release. So, you could consider the beta release as full release.

I plan to skip the full release and do the Lucid instead.

DK

---

### Post by Coglin on 2010-04-27
Thanks - look forward to it .... :)
 
any testing or other help a humble sys admin can be let me know

---

### Post by Coglin on 2010-06-29
HI DK and others
 
I was unable to get UCE server to run nicely on my virtual servers due to them being 64 bit ( albiet one is AMD and would load the 32 bit server version just could not control mouse or keyboard)
 
I have now tried another PC using your V 6.0 ( based on 9.10) as my previous CE net filter box was suffering HDD corruption :(
 
fresh install and enabling internet sharing worked great but as soon as i fix the NICs IP to be a static it wont allow any internet traffic either from itself or from clients with the IP:8080 as proxy setting.
 
I have found refernces on forums to the tinyproxy error being linked to loss of DNS, but the NIC still has DNS server set OK
 
was able to ping our DNS server from the CE box
 
cycled Dans guardian and found issue remained
 
Restarted box and found same issue
 
I have cleared firfox cache on both server and client
 
Any suggestion please?

---

### Post by david_kt on 2010-06-30
> **Coglin said:**
> HI DK and others
 
I was unable to get UCE server to run nicely on my virtual servers due to them being 64 bit ( albiet one is AMD and would load the 32 bit server version just could not control mouse or keyboard)
 
I have now tried another PC using your V 6.0 ( based on 9.10) as my previous CE net filter box was suffering HDD corruption :(
 
fresh install and enabling internet sharing worked great but as soon as i fix the NICs IP to be a static it wont allow any internet traffic either from itself or from clients with the IP:8080 as proxy setting.
 
I have found refernces on forums to the tinyproxy error being linked to loss of DNS, but the NIC still has DNS server set OK
 
was able to ping our DNS server from the CE box
 
cycled Dans guardian and found issue remained
 
Restarted box and found same issue
 
I have cleared firfox cache on both server and client
 
Any suggestion please?

Try to disable dansguardian, and see whether the internet connection is ok or not.

DK

---

### Post by Coglin on 2010-06-30
HI DK
 
no i haven't tried that as yet - i will try when out of core hours and can test
 
for now i have enabled it and just used the DHCP assigned IP in the Group policy to force office browsers through the UCE box
 
I am also curious about Remote desktop enabling on the box so i can administer the white list easily when working offsite ( which i do a fair bit)
 
using Synaptic PM i did install Vino as i had this on my old UCE box but it's not allowing connections - i assume because of the change in firewall it is being blocked?
 
i have tried accepting 5900 in iptables accordingly but its still not allowing connection from my LT
sudo iptables -A INPUT -p tcp --destination-port 5900 --source x.x.x.0/24 -j ACCEPT

---

