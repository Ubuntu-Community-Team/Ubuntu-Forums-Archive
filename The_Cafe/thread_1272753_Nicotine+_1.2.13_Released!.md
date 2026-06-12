---
title: "Nicotine+ 1.2.13 Released!"
date: 2009-09-22
forum: The Cafe
---

### Post by OffHand on 2009-09-22
We have released a new version of Nicotine+

[Download it here!]("http://www.nicotine-plus.org")

No deb available yet, but maybe someone can make one. It will be packaged eventually, but if you want to have the latest and greatest you will have to run it from source  ;)

[CHANGELOG]("http://www.nicotine-plus.org/browser/tags/1.2.13/doc/CHANGELOG")

:guitar:

---

### Post by kk0sse54 on 2009-09-22
Fantastic! Nicotine+ has been really coming along this last year or so. Uunfortunately the freebsd port hasn't been updated to the new release yet so I'll have to hold off from trying it.

---

### Post by OffHand on 2009-09-25
Glad you like it!

---

### Post by hoppipolla on 2009-09-25
Yay! I love Nicotine :)

---

### Post by commandant_gogo on 2009-09-25
Hi,

thanks, nice release, works fine with me.

I've got a little extra-question 'cause i'm new on soulseek. Does it allow SSL encryption?

---

### Post by moster on 2009-09-25
> **hoppipolla said:**
> Yay! I love Nicotine :)

Me too. Used to smoke a pack a day.

;)

---

### Post by hoppipolla on 2009-09-25
> **moster said:**
> Me too. Used to smoke a pack a day.

;)

haha yeah that kinda nicotine rules too! hehe :)

I can never be bothered to put the + on the end of the program name when I type or talk about it! :)

---

### Post by OffHand on 2009-09-25
> **commandant_gogo said:**
> Hi,

thanks, nice release, works fine with me.

I've got a little extra-question 'cause i'm new on soulseek. Does it allow SSL encryption?

No, it doesn't and I don't see it happening.

---

### Post by RiceMonster on 2009-09-25
Cool. Thanks for all your work on Nicotine+! It makes using soulseek on Linux as nice, or maybe even nicer than on Windows.

Should be getting this update in arch very soon.

---

### Post by Eisenwinter on 2009-09-25
> **RiceMonster said:**
> Cool. Thanks for all your work on Nicotine+! It makes using soulseek on Linux as nice, or maybe even nicer than on Windows.

Should be getting this update in arch very soon.
I'm waiting for the Arch update also.

I used 1.2.12 from source until I saw the Arch package, switched to that.

1.2.12 is good, so I'll just wait for the package instead of using the "messy" source approach.

---

### Post by OffHand on 2009-09-28
Bump!

---

### Post by razorboy5 on 2009-09-28
sry i read the definitions and descriptions of Nicotine+ after reading this post however i still cant seem to figure out what it does

could u explain in noob language what purpose it actually serves :p thx

---

### Post by RiceMonster on 2009-09-28
> **razorboy5 said:**
> sry i read the definitions and descriptions of Nicotine+ after reading this post however i still cant seem to figure out what it does

could u explain in noob language what purpose it actually serves :p thx

It's a soulseek client, which is a p2p network.

---

### Post by OffHand on 2009-09-28
> **razorboy5 said:**
> sry i read the definitions and descriptions of Nicotine+ after reading this post however i still cant seem to figure out what it does

could u explain in noob language what purpose it actually serves :p thx
The answer is usually a mouse click away ;) From the Soulseek website:

> Soulseek® is a unique ad-free, spyware free, and just plain free file sharing application.

One of the things that makes Soulseek® unique is our community and community-related features. Based on peer-to-peer technology, virtual rooms allow you to meet people with the same interests, share information, and chat freely using real-time messages in public or private.

Soulseek®, with its built-in people matching system, is a great way to make new friends and expand your mind!

Soulseek® does not endorse nor condone the sharing of copyrighted materials. You should only share and download files which you are legally allowed to or have otherwise received permission to share. By using this network you agree to this and the other rules which are linked to from this page. The intention of Soulseek® is to help unsigned and/or independent artists find a place in the ever-growing music industry, in a place where discussion and the creation of music can take place. Use of this network for illegal or infringing purposes is not permitted. Please share responsibly and help make Soulseek® a place where all artists can find a common ground. 

---

### Post by Bernard_ivo on 2009-10-02
Dear all,
I'm still running Nicotine 1.2.9 under ubuntu jaunty and I have the following problem which happened recently. While I was starting up several programmes on my laptop, some of them hanged I somehow realised that I ran out of disk space. (Downloading some stuff) Nicotine was one of the programmes that was freezing cause of the lack of space. However when cleaning up the HD, now my Nicotine won't start it stucks at futex_wait and that's it. I removed it twice (even complete removal), but it din not work out. I read that many other programmes have similar issues with futex_wait, but haven't found an answer how can I potentially overcome the trouble. Any suggestions - except using the new Nicotine source!

---

### Post by OffHand on 2009-10-02
We dont support 1.2.9 anymore. Either update to Ubuntu 9.10, use the
package from 9.10 or run from source :)

---

### Post by OffHand on 2009-10-03
NOTE: Depending on your OS and processor type the search in 1.2.13 might not work. Version 1.2.14 will fix this and should be released in a day or two.

---

### Post by Bernard_ivo on 2009-10-06
> **OffHand said:**
> We dont support 1.2.9 anymore. Either update to Ubuntu 9.10, use the
package from 9.10 or run from source :)

Well, 1.2.9+dfsg-3ubuntu1 is the only one in the universe packages repository for Ubuntu jaunty 9.04 (not mentioned at [http://nicotine-plus.org/wiki/NicotineOnDebian](http://nicotine-plus.org/wiki/NicotineOnDebian)) so it would've been good to release some newer deb package since you do not support the above version. And Ubuntu 9.10 is due to more than 20 days. Thanks for the advices though.

Cheers

---

### Post by OffHand on 2009-10-06
> **Bernard_ivo said:**
> Well, 1.2.9+dfsg-3ubuntu1 is the only one in the universe packages repository for Ubuntu jaunty 9.04 (not mentioned at [http://nicotine-plus.org/wiki/NicotineOnDebian](http://nicotine-plus.org/wiki/NicotineOnDebian)) so it would've been good to release some newer deb package since you do not support the above version. And Ubuntu 9.10 is due to more than 20 days. Thanks for the advices though.

Cheers

I am not an Ubuntu packager or MOTU and we have nothing to to with Ubuntu specifically (Linux in general yes). N+ devs and packagers have full time jobs or studies and do this in their free time :)

If you want to help out though, you can start using svn and report bugs and/or look into building debian/ubuntu packages :guitar:

---

### Post by Bernard_ivo on 2009-10-06
We are all busy that is for sure, so I also do what I can do. Nevertheless since you are advertising N+ at Ubuntu forums, presumably for Ubuntu users I thought a deb package will be available :) . Currently there is a deb file but for Ubuntu 9.10 which as we all now is only Beta at the moment) Not all ubuntu users can (or have time to) work with source, install tgz or others different than Synaptec or package manager. I do appreciate what many people do for the open source world and the limitations which we all face, so keep the good work.

Cheers

---

### Post by -grubby on 2009-10-06
> **Bernard_ivo said:**
> We are all busy that is for sure, so I also do what I can do. Nevertheless since you are advertising N+ at Ubuntu forums, presumably for Ubuntu users I thought a deb package will be available :) . Currently there is a deb file but for Ubuntu 9.10 which as we all now is only Beta at the moment) Not all ubuntu users can (or have time to) work with source, install tgz or others different than Synaptec or package manager. I do appreciate what many people do for the open source world and the limitations which we all face, so keep the good work.

Cheers

It's written in Python. As long as the dependencies are met it will run without compilation.

It also comes with an installer, setup.py (run python setup.py install to install)

---

### Post by Bernard_ivo on 2009-10-06
Thanks, dependency problem occured Error: Dependency is not satisfiable: python-support (>= 0.90.0) current version in jaunty is 0.8.7ubuntu4. 

I've never compiled something from source code, so a How To will be needed. 

Cheers

---

### Post by -grubby on 2009-10-06
> **Bernard_ivo said:**
> Thanks, dependency problem occured Error: Dependency is not satisfiable: python-support (>= 0.90.0) current version in jaunty is 0.8.7ubuntu4. 

I've never compiled something from source code, so a How To will be needed. 

Cheers
Ivo

You're not compiling anything, as I said, it's written in Python. All the installer does is copy some files to special places and probably add menu entries.

Anyways, I don't know if you'll be able to get past that error without using Karmic.

---

### Post by Bernard_ivo on 2009-10-06
I tried this,
I unpacked nicotine+-1.2.12.tar.gz it and ran the setup.py, 
it looked it did not make all as expected 
/Failed to import the Mutagen library, falling back to old library. To improve meta data please install Mutagen./usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'windows'/ Files were copied in usr/share/nicotine/..... but still the same problem futex_wait.
I have some config.old (backup file) from the day it crashed, but not sure whether I can get any use of it.

---

### Post by OffHand on 2009-10-06
> **Bernard_ivo said:**
> I tried this,
I unpacked nicotine+-1.2.12.tar.gz it and ran the setup.py, 
it looked it did not make all as expected 
/Failed to import the Mutagen library, falling back to old library. To improve meta data please install Mutagen./usr/lib/python2.6/distutils/dist.py:266: UserWarning: Unknown distribution option: 'windows'/ Files were copied in usr/share/nicotine/..... but still the same problem futex_wait.
I have some config.old (backup file) from the day it crashed, but not sure whether I can get any use of it.

We are already up to version 1.2.14:

1) Download Nicotine+ from here:

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

2) Extract it to your home folder

3) Open your terminal

4) cd nicotine+-1.2.14 (or wherever you have extracted it)

5) ./nicotine

6) You can make a launcher using this path: /home/username/nicotine+ folder/nicotine  (do this with System > Preferences > Main Menu)

---

### Post by OffHand on 2009-10-06
Also:

```
sudo apt-get install python-mutagen
```

---

### Post by Bernard_ivo on 2009-10-06
> **OffHand said:**
> 
5) ./nicotine 
./nicotine.py worked
result is:
Tue 18:09 Nicotine supports "psyco", an inline optimizer for python code, you
          can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
location: /usr/lib/xulrunner-1.9.0.14/libxpcom.so 
before 3
Traceback (most recent call last):
  File "./nicotine.py", line 275, in <module>
    run()
  File "./nicotine.py", line 261, in run
    app = frame.MainApp(config, plugins, trayicon, tryrgba, hidden, webbrowser)
  File "/home/bernard/nicotine+-1.2.14/pynicotine/gtkgui/frame.py", line 3604, in __init__
    self.frame = NicotineFrame(config, plugindir, trayicon, rgbamode, start_hidden, WebBrowser)
  File "/home/bernard/nicotine+-1.2.14/pynicotine/gtkgui/frame.py", line 328, in __init__
    self.np = NetworkEventProcessor(self, self.callback, self.logMessage, self.SetStatusText, config)
  File "/home/bernard/nicotine+-1.2.14/pynicotine/pynicotine.py", line 118, in __init__
    self.shares = Shares(self)
  File "/home/bernard/nicotine+-1.2.14/pynicotine/shares.py", line 28, in __init__
    self.CompressShares("normal")
  File "/home/bernard/nicotine+-1.2.14/pynicotine/shares.py", line 83, in CompressShares
    m.makeNetworkMessage(nozlib=0, rebuild=True)
  File "/home/bernard/nicotine+-1.2.14/pynicotine/slskmessages.py", line 1512, in makeNetworkMessage
    msg = msg + self.packObject(len(self.list.keys()))
  File "/usr/lib/python2.6/shelve.py", line 101, in keys
    return self.dict.keys()
  File "/usr/lib/python2.6/bsddb/__init__.py", line 300, in keys
    return _DeadlockWrap(self.db.keys)
  File "/usr/lib/python2.6/bsddb/dbutils.py", line 68, in DeadlockWrap
    return function(*_args, **_kwargs)
DBPageNotFoundError: (-30986, 'DB_PAGE_NOTFOUND: Requested page not found')


>  6) You can make a launcher using this path: /home/username/nicotine+ folder/nicotine  (do this with System > Preferences > Main Menu)

I made a link to the path but the programme is not started. 

I still have 1.2.9 installed though not sure that is the problem.(I did remove it and after starting nicotine.py nothing happens except that in Systemt monitor Waiting Channel it says do_stop_signal) no programme launched

---

### Post by OffHand on 2009-10-06
Ok. Leave Nicotine+ from the repository installed but close it. Then do the following:

```

chmod +x versionbump_nicotine.sh

```
```

sudo sh versionbump_nicotine.sh

```
Revert back to repo version
```
sudo rm /usr/bin/nicotine
sudo dpkg-divert --rename --remove /usr/bin/nicotine
sudo rm -r /opt/nicotine+-*

```

[Download script]("http://dl.getdropbox.com/u/291902/versionbump_nicotine.sh")

---

### Post by zkaje on 2009-10-29
I have same problem.
When i launched nicotine, there appeared two processes in system monitor and no interface (same error message in terminal)
After i've done all that said OffHand, nothing changed except that now there appeares only one process in system monitor.
Help please.

---

### Post by OffHand on 2009-10-29
> **zkaje said:**
> I have same problem.
When i launched nicotine, there appeared two processes in system monitor and no interface (same error message in terminal)
After i've done all that said OffHand, nothing changed except that now there appeares only one process in system monitor.
Help please.

When did you try to run the script? And when did you download it?

I have upped the script to version 1.2.14

---

### Post by zkaje on 2009-10-29
> **OffHand said:**
> When did you try to run the script? And when did you download it?

I have upped the script to version 1.2.14

Ii did it about 3-4 days ago.
And have redone all this steps just now. Same result :/

---

### Post by OffHand on 2009-10-29
> **zkaje said:**
> Ii did it about 3-4 days ago.
And have redone all this steps just now. Same result :/

Do you have N+ from te repositories installed? Can you check if there is a N+ folder in /opt?

---

### Post by zkaje on 2009-10-29
> **OffHand said:**
> Do you have N+ from te repositories installed? Can you check if there is a N+ folder in /opt?
There is no N+ folder in /opt/
How can i know if i have it installed from repositories?

---

### Post by OffHand on 2009-10-29
> **zkaje said:**
> There is no N+ folder in /opt/
How can i know if i have it installed from repositories?

System > Administration > Synaptic

Do a search for nicotine. The script assumes you have it installed.

---

### Post by zkaje on 2009-10-29
> **OffHand said:**
> System > Administration > Synaptic

Do a search for nicotine. The script assumes you have it installed.

In synaptic it is written that version 1.2.9+dfsg-3ubuntu1 is installed
N+ worked well untill one day it stopped launching interface :( first time i installed it the way "sudo apt-get install nicotine".

---

### Post by OffHand on 2009-10-29
> **zkaje said:**
> In synaptic it is written that version 1.2.9+dfsg-3ubuntu1 is installed
N+ worked well untill one day it stopped launching interface :( first time i installed it the way "sudo apt-get install nicotine".

Ok, I just tested the script again and it works flawless. Please reinstall N+ from Synaptic and launch it. Does that work? If not go to [www.nicotine-plus.org](www.nicotine-plus.org) and open a new ticket. If you open a new ticket launch nicotine from the terminal and post any tracebacks. The command you need to issue is nicotine

---

### Post by zkaje on 2009-10-29
> **OffHand said:**
> Ok, I just tested the script again and it works flawless. Please reinstall N+ from Synaptic and launch it. Does that work? If not go to [www.nicotine-plus.org]("http://www.nicotine-plus.org") and open a new ticket. If you open a new ticket launch nicotine from the terminal and post any tracebacks. The command you need to issue is nicotine

I dont have permission to create a ticket. Tracebacks are:


> Thu 23:38 Nicotine supports "psyco", an inline optimizer for python code, you
          can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
&#1063;&#1090;&#1074; 23:38 Failed to import the Mutagen library, falling back to old library.
          To improve meta data please install Mutagen.
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 275, in <module>
    run()
  File "/usr/bin/nicotine", line 261, in run
    app = frame.MainApp(config, plugins, trayicon, tryrgba, hidden, webbrowser)
  File "/opt/nicotine+-1.2.14/pynicotine/gtkgui/frame.py", line 3604, in __init__
    self.frame = NicotineFrame(config, plugindir, trayicon, rgbamode, start_hidden, WebBrowser)
  File "/opt/nicotine+-1.2.14/pynicotine/gtkgui/frame.py", line 328, in __init__
    self.np = NetworkEventProcessor(self, self.callback, self.logMessage, self.SetStatusText, config)
  File "/opt/nicotine+-1.2.14/pynicotine/pynicotine.py", line 118, in __init__
    self.shares = Shares(self)
  File "/opt/nicotine+-1.2.14/pynicotine/shares.py", line 28, in __init__
    self.CompressShares("normal")
  File "/opt/nicotine+-1.2.14/pynicotine/shares.py", line 83, in CompressShares
    m.makeNetworkMessage(nozlib=0, rebuild=True)
  File "/opt/nicotine+-1.2.14/pynicotine/slskmessages.py", line 1512, in makeNetworkMessage
    msg = msg + self.packObject(len(self.list.keys()))
  File "/usr/lib/python2.6/shelve.py", line 101, in keys
    return self.dict.keys()
  File "/usr/lib/python2.6/bsddb/__init__.py", line 300, in keys
    return _DeadlockWrap(self.db.keys)
  File "/usr/lib/python2.6/bsddb/dbutils.py", line 68, in DeadlockWrap
    return function(*_args, **_kwargs)
DBPageNotFoundError: (-30986, 'DB_PAGE_NOTFOUND: Requested page not found')


---

### Post by OffHand on 2009-10-30
If you upgrade to Ubuntu 9.10 you will get version 1.2.12 in the repositories. 1.2.9 is not supported anymore, it's just too old (we are working on version 1.2.15).

Cheers,
OffHand

---

### Post by zkaje on 2009-10-30
> **OffHand said:**
> If you upgrade to Ubuntu 9.10 you will get version 1.2.12 in the repositories. 1.2.9 is not supported anymore, it's just too old (we are working on version 1.2.15).

Cheers,
OffHand

Thanks for your attention.
How do you think, is there any way for me to get back N+ working?

---

### Post by OffHand on 2009-10-30
> **zkaje said:**
> Thanks for your attention.
How do you think, is there any way for me to get back N+ working?

Upgrading to Ubuntu 9.10 (and thus to N+ 1.2.12) would be a step in the right direction...

---

### Post by OffHand on 2009-10-31
> **zkaje said:**
> Thanks for your attention.
How do you think, is there any way for me to get back N+ working?

You can also try the .[deb]("http://dl.getdropbox.com/u/291902/nicotine_1.2.14-1_i386.deb") file one of our devs made...

---

### Post by JoZ3 on 2009-11-02
any .deb to karmic x64???

---

### Post by Eisenwinter on 2009-11-02
I'm already on 1.2.15 from svn ;) 

Really nice work. GUI has been cleaned up and made easier to navigate through. I'm not sure how *.13 and *.14 were, because I haven't used them. I jumped straight from *.12 to the svn version, which is 1.2.15.

---

### Post by OffHand on 2009-11-02
> **JoZ3 said:**
> any .deb to karmic x64???

It will probably work on a 64 bit system. Doesn't hurt to give it a try  ;)

---

