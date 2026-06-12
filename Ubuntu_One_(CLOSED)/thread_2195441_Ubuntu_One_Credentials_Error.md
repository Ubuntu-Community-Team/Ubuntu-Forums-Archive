---
title: "Ubuntu One: Credentials Error"
date: 2013-12-24
forum: Ubuntu One (CLOSED)
---

### Post by Wojtekenson on 2013-12-24
I'm trying to get into Ubuntu One, however, when I open up the program I get an error.

 CredentialsError
 DBusException(dbus.String(u'Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1'),)

The prompt happens before anything pops up about logging in. It just remains grey and lets me know this error has occured and that is must close. I've reinstalled Ubuntu one via:

sudo apt-get purge ubuntuone-client
sudo apt-get install ubuntuone-client

No change. I've even reinstalled it by clicking on the executable which remains on my computer after I've uninstalled. I also accidently removed python via 

sudo apt-get purge python 

because I read somewhere that someone was getting this error after they installed a python package. Obviously, as I know now, this made a lot of things on my computer not work and so I ctrl+alt+f1 and reinstalled the desktop and well that is where I am now. I just would like to get ubuntu one to work so I can install some new things. I received this notebook recently with ubuntu 12.04 pre-installed. Also I'm a fairly new user but help would be much appreciated. I've also googled this problem and can't seem to find a fix. 

Thanks for reading this

~Charles Stevenson

---

### Post by Irihapeti on 2013-12-24
*Thread moved to **Ubuntu One**.*

---

### Post by Irihapeti on 2013-12-24
Looking at a [similar problem]("http://ubuntuforums.org/showthread.php?t=2155880") (involving the Software Center and Ubuntu One), it might be worth reinstalling python-sip and python-qt4. If it doesn't work, it's unlikely to do any harm.

---

### Post by Wojtekenson on 2013-12-24
I'm really having a lot of trouble installing these packages. I read the install instructions, but I can never get the 'make' command to work. I know I'm in the correct directory and I go through the install direction, in the index file for example of Qt4Qt5. It is just I can't seem to get any command to be accepted by the terminal to push this installation forward. I just don't know how to figure out what I'm missing. Any suggestions?

---

### Post by nothingspecial on 2013-12-24
Hi,

You shouldn't need to "make" anything, you can install these things with a package manager.

Also, you should not have to click an executable to install anything.

Do you have a Ubuntu One account set up ?

---

### Post by Wojtekenson on 2013-12-24
I do, but thats my problem in the first place is I get a credential error and ubuntu one closes. Therefore I can't get even utilize ubuntu ones function. It also doesn't allow me to even type in my credentials.

---

### Post by iraj.2535 on 2013-12-28
Having the same problem here. I'm a beginner in ubuntu and linux, and this was my first attempt to use ubuntu one client.

This is what I get:
> Sorry, an error has occurred and Ubuntu One needs to close.

CredentialsError

DBusException(dbus.String(u'Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1'),)

I appreciate any advice on this problem.

---

### Post by Wojtekenson on 2013-12-29
Okay I found a post that may give a clue in how I can fix this. 

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/711162](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/711162)

It seems that some files are in the wrong location or atleast are being called from an improper location. I must have done this when I installed a python package to my computer. Oops, right? Anyway I am still illiterate as how to fix this. Can any one with more experience help me out?

Thanks!

FOUND A FIX!!
Something is I think messed up was with how Ubuntu one was calling the python scripts in order to match your credentials with the SSO client. (I really don't know if this is accurate). But anyway type:


which python

if the output is: usr/local/bin/python
then most likely you'll get the error stated above by iraj.2535. 

My fix was simply to remove python from the local directory, but I made sure python existed in usr/bin/python first. That command was

rm usr/local/bin/python

Then double check which python
and if you get this output:

usr/bin/python

then the error should go away and your credentials should go through. 

Wow, that took a long time for a newbie to figure out. >_<
Hope this helps someone else in the future!

---

### Post by iraj.2535 on 2013-12-29
OK Wojtekenson, or if I may call you, Charles,

You are my hero!
I'm an absolute newbie (and if you call yourself a newbie I should find a more appropriate word!).
 This problem came up for me while I was trying to figure out my problem with SPE and wxPython ([my post]("http://ubuntuforums.org/showthread.php?t=2196481")).

And guess what! Your solution solved my original problem as well as this one.

I'm so happy!!!
Thanks again!

---

