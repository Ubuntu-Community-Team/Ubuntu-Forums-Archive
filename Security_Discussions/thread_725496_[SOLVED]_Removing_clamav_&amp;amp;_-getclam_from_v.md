---
title: "[SOLVED] Removing clamav &amp;amp; -getclam from /var/lib after uninstall?"
date: 2008-03-15
forum: Security Discussions
---

### Post by valjour on 2008-03-15
:confused: Pete here; Hi.

I'm a part of a green bean and  was wondering if I could get some help.

Got a variety  of error messages from several parts  after installing clamav about a month ago.  I used synoptic and apt-get  to un/install  it and other complimentary components.  I did a full uninstall as my final synoptic gesture and proceeded to install Avast a couple days later without a hitch.  I am proud of myself because I went to the Avast  site and installed it seamlessly  through apt-get about two weeks ago.

When I ran Avast (finally)  early this week after I followed a suggestion and linked my email to Thunderbird I got  a message that 'eicar Test- Not virus!' was found in /var/lib/clamav-getfiles.  when I poked around in the file (through Places search) I found both files [clam av & -getfiles]..  Avast told me that it could do nothing with the "dirty" file during the scan when I asked it to remove it.

I was surfing the web last night and then attempted to clean up my bookmarks and my computer started acting sluggish and weird.  I don't know if it be fate or linked.

I hit some Fkey (fat-fingered) looking for the run command line and a full screen bash window opened and told me I had mail.  It took me a while to figure it out but it wasn't coming from my Thunderbird in box.  My machine wished to speak so I let it when I finally understood. 

The messages all said the same thing (all 8)  about clamav and some rotating file.  I wrote down exactly what it said but can not find it.  There it is. 

 /etc/cron.daily/logrotate error: clam-daemon :6 unknown user/clamav
Run parts: /etc/cron.daily/logrotate exited with return code 1.

A friend with some Ubuntu and command line experience came over .He tried to explain cron but it went through me like a sieve.  I could not duplicate where I went to find the files.   We cleaned, upgraded and the lot with apt-get commands.  It kept on telling us that clamav could not be found. 

Through my adventures I have found out that clam is at debian-exim and -get- files is at root as far as permissions go.  I am a little intimidated by this.

Today I ran Avast out of curiosity.  It found that file and folder again (system scan) so I could retrace my steps and let you know where it lived. Today however Avast let me put it in the "chest"-  I wish all traces of clamav gone if that is possible can you help me?  It has caused me nothing but grief. Avast installed easily, is trouble-free so far, and works like a charm for my current  tastes and abilities.

Could this be posted in ABT forum too? It might help someone out there as well..

Thanks Pete

---

### Post by mikewhatever on 2008-03-15
Can you post the output of <locate clam> and <cat /etc/logrotate.conf>.

---

### Post by valjour on 2008-03-16
Thanks MikeWhatever

Here is the output generated:

pw@pw-desktop:~$ sudo locate clam
[sudo] password for pw:
/usr/share/app-install/desktop/clamtk.desktop
/home/pw/Documents/firsttermuseforclam.odt
/home/pw/.clamtk
/home/pw/.clamtk/viruses
/home/pw/.clamtk/history
/var/lib/clamav
/var/lib/clamav/main.inc
/var/lib/clamav/main.inc/main.mdb
/var/lib/clamav/main.inc/main.hdb
/var/lib/clamav/main.inc/main.ndb
/var/lib/clamav/main.inc/COPYING
/var/lib/clamav/main.inc/main.db
/var/lib/clamav/main.inc/main.zmd
/var/lib/clamav/main.inc/main.fp
/var/lib/clamav/main.inc/main.info
/var/lib/clamav/mirrors.dat
/var/lib/clamav/daily.inc
/var/lib/clamav/daily.inc/daily.db
/var/lib/clamav/daily.inc/daily.cfg
/var/lib/clamav/daily.inc/daily.zmd
/var/lib/clamav/daily.inc/daily.hdu
/var/lib/clamav/daily.inc/daily.mdb
/var/lib/clamav/daily.inc/COPYING
/var/lib/clamav/daily.inc/daily.hdb
/var/lib/clamav/daily.inc/daily.pdb
/var/lib/clamav/daily.inc/daily.ndb
/var/lib/clamav/daily.inc/daily.ftm
/var/lib/clamav/daily.inc/daily.mdu
/var/lib/clamav/daily.inc/daily.fp
/var/lib/clamav/daily.inc/daily.ndu
/var/lib/clamav/daily.inc/daily.info
/var/lib/clamav/daily.inc/daily.wdb
/var/lib/ucf/cache/:etc:logrotate.d:clamav-daemon
/var/lib/ucf/cache/:etc:clamav:freshclam.conf
/var/lib/clamav-getfiles
/var/lib/clamav-getfiles/installedfiles
/var/lib/dpkg/info/clamav-freshclam.postrm
/var/lib/dpkg/info/clamav-freshclam.list
/var/lib/dpkg/info/clamav-daemon.list
/var/lib/dpkg/info/clamtk.postrm
/var/lib/dpkg/info/clamtk.list
/var/lib/dpkg/info/clamav-getfiles.list
/var/lib/dpkg/info/clamav-getfiles.postrm
/var/lib/dpkg/info/clamav-milter.list
/var/lib/dpkg/info/clamav-milter.postrm
/var/lib/dpkg/info/clamav-daemon.postrm
/var/log/clamav
/var/log/clamav/freshclam.log
/var/log/clamav/freshclam.log.1
/var/log/clamav/freshclam.log.2.gz
/etc/clamav
/etc/clamav/freshclam.conf
/etc/clamav/clamav-base.init
/etc/rc1.d/K20clamav-freshclam
/etc/rc1.d/K20clamav-milter
/etc/rc1.d/K20clamav-daemon
/etc/init.d/clamav-freshclam
/etc/init.d/clamav-daemon
/etc/init.d/clamav-milter
/etc/ppp/ip-down.d/clamav-freshclam-ifupdown
/etc/ppp/ip-up.d/clamav-freshclam-ifupdown
/etc/network/if-down.d/clamav-freshclam-ifupdown
/etc/network/if-up.d/clamav-freshclam-ifupdown
/etc/rc2.d/S20clamav-milter
/etc/rc2.d/S20clamav-daemon
/etc/rc2.d/S20clamav-freshclam
/etc/logrotate.d/clamav-freshclam
/etc/logrotate.d/clamav-daemon
/etc/rc0.d/K20clamav-freshclam
/etc/rc0.d/K20clamav-milter
/etc/rc0.d/K20clamav-daemon
/etc/logcheck/ignore.d.server/clamav-freshclam
/etc/logcheck/ignore.d.server/clamav-daemon
/etc/logcheck/ignore.d.server/clamav-milter
/etc/logcheck/ignore.d.paranoid/clamav-daemon
/etc/logcheck/ignore.d.paranoid/clamav-milter
/etc/rc3.d/S20clamav-milter
/etc/rc3.d/S20clamav-daemon
/etc/rc3.d/S20clamav-freshclam
/etc/default/clamav-daemon
/etc/default/clamav-milter
/etc/rc5.d/S20clamav-milter
/etc/rc5.d/S20clamav-daemon
/etc/rc5.d/S20clamav-freshclam
/etc/rc6.d/K20clamav-freshclam
/etc/rc6.d/K20clamav-milter
/etc/rc6.d/K20clamav-daemon
/etc/mail/m4/clamav-milter.m4
/etc/rc4.d/S20clamav-milter
/etc/rc4.d/S20clamav-daemon
/etc/rc4.d/S20clamav-freshclam
pw@pw-desktop:~$ cat/etc/logrotate.conf
bash: cat/etc/logrotate.conf: No such file or directory
pw@pw-desktop:~$

---

### Post by mikewhatever on 2008-03-17
I remember having a similar problem with left over files when I installed VLC through Add/Remove, but un-installed it throgh apt-get. Installing it back and then removing though Add/Remove did remove almost all.

<**cat /etc/logrotate.conf**> there is a space between cat and /.

---

### Post by valjour on 2008-03-17
Hey Mike,

Sorry I didn't pick up on that space.  Here is the output.

pw@pw-desktop:~$ sudo cat /etc/logrotate.conf 
[sudo] password for pw:
# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

# system-specific logs may be configured here
pw@pw-desktop:~$ 


I iun/installed (both)  it through synaptic not applications.  Then tried too un/install (Both)  through apt-get if I am not mistaken.  It was about a month ago that I started the process to see if I could utilize  clam.

Do you think I should try the add/remove thing before we reassess?

Pete

---

### Post by valjour on 2008-03-18
:KS  Mikewhatever,

I went back in to Synaptic searched clam  and when I studied all the output carefully  I noticed that the " mark for complete removal" option was sttill available on 5 sets: (Wish I could use the command line with this proficiency- someday...hopefully sooner than I think)

(clamav)-daemon, freshclam, getfiles, milter, and clamtk.  I selected this option setting on all the mentioned products.  I rebooted the system and ran the terminal.  The process was as follows:

clamav-daemon will be removed with configuration 
clamav-freshclam will be removed with configuration 
clamav-getfiles will be removed with configuration 
clamav-milter will be removed with configuration 
clamtk will be removed with configuration 

terminal in synaptic would not let me copy details.

Then I rebooted (microsludge habit) then reran commands that you asked for again:  Here is the resultant data:

pw@pw-desktop:~$ sudo locate clam
[sudo] password for pw:
/usr/share/app-install/desktop/clamtk.desktop
/home/pw/Documents/firsttermuseforclam.odt
/home/pw/.clamtk
/home/pw/.clamtk/viruses
/home/pw/.clamtk/history
/var/lib/clamav
/var/lib/clamav-getfiles
/var/lib/clamav-getfiles/installedfiles
/var/log/clamav
/etc/clamav
/etc/clamav/clamav-base.init
pw@pw-desktop:~$ 
pw@pw-desktop:~$ 
pw@pw-desktop:~$ sudo cat /etc/logrotate.conf
# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

# system-specific logs may be configured here
pw@pw-desktop:~$



Its been a long nite I'm turning in for a few' before work


I'd appreciate your input when you get  a sec. I'm willing to learn beyond my friends super nword removal suggestion.. I wish to learn thinking peoples commands (At least at first;)).

Thanks for your patience, kindness and care,

And oh yeah did I mention thought and  time on this one?

---

### Post by mikewhatever on 2008-03-18
Well, congratulations. It looks like there is not much of clam left on your system. It's now easy to manually remove the leftovers:
<rm -r .clamtk>
<sudo rm -r /var/lib/clamav>
<sudo rm -r /var/lib/clamav-getfiles>
<sudo rm -r /var/log/clamav>
<sudo rm -r /etc/clamav>

That should be the end of clam.

---

### Post by valjour on 2008-03-18
Hi Mikewhatever,

Thanks for the good news.  Could it be that clamtk was the culprit all along? This is the output I got:


pw@pw-desktop:~$ sudo rm -r .clamtk
[sudo] password for pw:
pw@pw-desktop:~$ sudo rm -r var/libclamav
rm: cannot remove `var/libclamav': No such file or directory
pw@pw-desktop:~$ sudo rm -r var/lib/clamav
rm: cannot remove `var/lib/clamav': No such file or directory
pw@pw-desktop:~$ sudo rm -r var/lib/clamav-getfiles
rm: cannot remove `var/lib/clamav-getfiles': No such file or directory
pw@pw-desktop:~$ sudo rm -r var/log/clamav
rm: cannot remove `var/log/clamav': No such file or directory
pw@pw-desktop:~$ sudo rm -r etc/clamav
rm: cannot remove `etc/clamav': No such file or directory
pw@pw-desktop:~$ 

Well var/lib, var/log and etc  files still exist.  Aah I see the problem...
no " /" (root indicator- for lack of a better word).  Let's give it a whirl.

They are gone! See!:

pw@pw-desktop:~$ sudo rm -r /etc/clamav
pw@pw-desktop:~$ sudo rm -r /var/log/clamav
pw@pw-desktop:~$ sudo rm -r /var/lib/clamav-getfiles
pw@pw-desktop:~$ sudo rm -r /var/log/clamav
rm: cannot remove `/var/log/clamav': No such file or directory
#because its really gone! fat-fingered the up/enter combo
pw@pw-desktop:~$ 
pw@pw-desktop:~$ 
pw@pw-desktop:~$ sudo rm -r /var/lib/clamav
pw@pw-desktop:~$ 

Thanks Mike whatever. You :guitar:

Problem solved.

---

### Post by valjour on 2008-03-18
OOps, Almost forgot what you taught me in the beginning:


pw@pw-desktop:~$ sudo locate clam
[sudo] password for pw:
/usr/share/app-install/desktop/clamtk.desktop
/home/pw/Documents/clam uninstall.odt
/home/pw/Documents/firsttermuseforclam.odt
pw@pw-desktop:~$ 


can not manually locate  clamtk.desktop in the file. ( it is not there before claws...)

Want to get into good habits and learn the command line but some times it fibs.:)

Thanks again.

---

### Post by mikewhatever on 2008-03-19
With time, you'll get more comfortable with CLI, especially if you are interested. Take care.

---

### Post by valjour on 2008-03-28
Thanks for helping me solve my first issue Mikewhatever.

---

