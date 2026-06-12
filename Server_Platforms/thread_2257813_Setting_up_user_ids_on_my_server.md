---
title: "Setting up user ids on my server"
date: 2014-12-22
forum: Server Platforms
---

### Post by ecowan on 2014-12-22
I have a server on my home network that I use for several functions. It runs squid and dansguardian to filter what my teenage kids get up to. It hoists my printers and scanners. It has a couple of large capacity hard drives where I keep my photos, music, videos and ebooks.

I want to run a couple of server tasks, one calibre-server to manage my ebooks, and one rygel to stream music and video to my 'phone, laptop or TV.

I need the human users defined so that squid can verify their passwords and then check various other constraints based on whether the user is a kid or an adult. But I don't want anyone but the administrator to be able to sign on and run programs.

I want to run the ebook and DNLA servers under a special id that cannot be used to login or run a shell.

I've been reading man pages, Ubuntu wiki, etc. etc. but it feels like I'm trying to follow strands of spaghetti around.

Can someone give me some hints, suggestions or links?

Thanks. - Erny

---

### Post by TheFu on 2014-12-23
The most common way to prevent an account from getting a shell at login is to use /bin/false at the shell in the /etc/passwd file.  This also means that only root (or sudo) can be used to start/stop processes running under that userid.  Some "service accounts" like for your ebook server may require a shell - I don't know.  For DLNA servers ... I don't think a shell is needed - cannot check this for a few days, sorry.

Can't help with squid - I've only setup the trivial methods, but would think non-system accounts can be used for proxy authentication. You are not the first with that requirement. If squid doesn't use system accounts, then the users won't be able to ssh into the machine.

Getting a hang of user accounts can take some time, but it will come. Much of this stuff is based on normal UNIX/Linux user file and directory permissions, so learn that stuff from a good resource, practice understanding and setting the different permissions across different groups and accounts. It will save you weeks, if not months, of frustration. There are many subtle settings that have desirable outcomes which become intuitive AFTER seeing the setting in action.

The problem with searching for specific answers is that topics don't lead into the next and the next. Building knowledge in a smart order. That is where books really can save time.  There is a free pdf book on "linux command line" - you can also buy it at any bookstore which provides the guided learning - not just what to type, but WHY, so the commands make more sense and are easier to recall later due to the context.  I've been telling folks to READ the first 100 pgs, then skim the rest of the book - 1 pg every half second to get a feel for the other capabilities. Knowing what is possible is a big deal. Only later when you need that specific knowledge is it worth READING.  Plus by the location in this book, an estimate of the skill level is implied. Things on page 120 are easier and more fundamental than things on page 300.

Anyway, hope this helps.

---

### Post by ecowan on 2014-12-23
It certainly does help. Thank you for taking the time. I'm not actually running Ubuntu Sever, but Ubuntu Desktop 14.04, which I should have said.

I have squid working fine, using basic authorization. 

I tried defining a user id for my media server using adduser , but lightdm then showed it on the login greeting screen. I looked into lightdm configuration, but /etc/lightdm/users.conf warns me that settingser there will be ignored because I have AccountsService. I can't find any documentation on how to configure AccountsService. I did find a reference to /usr/share/lightdm/lightdm.conf.d/... but that also said not to edit anything there.

Should I edit /etc/passwd directly?

How can I keep lighdm from offering up a user on the greeting screen?

Thanks again for your advice.

---

### Post by TheFu on 2014-12-24
I would edit passwd directly. It is just a text file and that is the shorted way.
Don't know anything about lightdm - don't use it.
Don't know anything about AccountsService - don't use it.

I don't run any ubuntu desktops, just servers with plain window-managers. All the other options are too bloated to be considered, IMHO.

---

### Post by ecowan on 2014-12-24
Thank you for your reply.

---

### Post by TheFu on 2014-12-27
> **ecowan said:**
> Thank you for your reply.

Please mark thread as solved, if solved.

---

### Post by ecowan on 2014-12-27
Actually, I still hope for some hints.
My 'server' actually runs desktop, and so lightdm. So I'm still trying to figure out 
- how to keep user ids from showing up on the greeter screen
- how to suppress the execution of a shell

---

### Post by TheFu on 2014-12-27
> **ecowan said:**
> Actually, I still hope for some hints.
My 'server' actually runs desktop, and so lightdm. So I'm still trying to figure out 
- how to keep user ids from showing up on the greeter screen
- how to suppress the execution of a shell

Edit the passwd file and set the shell to /bin/false. That has worked for 30+ yrs.

There is a config file for each greeter .... everyone that I've seen has a lower-bound number for uids - anything less than that number will not be displayed on the login chooser. Think the default is 1000 on ubuntu. There is also a way to shutoff the usename chooser completely so everyone has to type both the userid and password to login. The config files that I've touched have example settings inside.   /etc/lightdm/lightdm.conf and /etc/lightdm/users.conf are the locations, may need to disable the Accounts Service crap.  Don't know what it is and I've never used it in 30+ yrs.

What have you tried? Did it work? Any log messages?

---

### Post by sandyd on 2014-12-27
> **ecowan said:**
> Actually, I still hope for some hints.
My 'server' actually runs desktop, and so lightdm. So I'm still trying to figure out 
- how to keep user ids from showing up on the greeter screen
- how to suppress the execution of a shell

Just remove the user id list.
See [http://www.webupd8.org/2014/08/lightdm-how-to-disable-user-list-or.html](http://www.webupd8.org/2014/08/lightdm-how-to-disable-user-list-or.html) for steps.

Regards,

---

### Post by ecowan on 2014-12-28
Thank you for that link. It's very informative. I'll try it out later today. - Erny

---

### Post by ecowan on 2015-01-07
See corrected reply below.

---

### Post by ecowan on 2015-01-07
So I finally tried the method described in the link above, and it does modify the greeter screen (once I created the correct sub-directory).
Thank you ever so much.

---

### Post by ecowan on 2015-01-09
So I have figured out how to get squid to authenticate a user without having the user set up as a normal Ubuntu desktop user.
In /etc/squid3/squid.conf I changed  
auth_param basic program /usr/lib/squid3/basic_pam_auth
to 
auth_param basic program /usr/lib/squid3/basic_ncsa_auth /etc/squid3/ncsa.passwd

and I used htpasswd to set up users and passwords in /etc/squid3/ncsa.passwd

Now the users do not show up on the server's greeting screen, and they can't login on the server.

Still trying to figure out how to run calibre-server and rygel on the server with a unique userid, and NOT as ROOT.

---

### Post by ecowan on 2015-01-09
Got it!
I wanted to set up media servers with special userids because they run all the time, listening for activity on some port.
So I defined a unique userid using "adduser --system --no-create-home --disabled-login --shell /bin/false userxyz" and set up calibre-server.conf and rygel-server.conf in /etc/init with a stanza "setuid userxyz".

Thank you for all your helpful suggestions.

---

