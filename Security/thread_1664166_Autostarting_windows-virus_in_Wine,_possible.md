---
title: "Autostarting windows-virus in Wine, possible?"
date: 2011-01-10
forum: Security
---

### Post by DanneStrat on 2011-01-10
Hi!

I have a question.

I've read numerous posts about viruses running in wine. 

Since Wine recognize the .exe filetype and associates itself with it, 

is it possible to get a virus that starts up automatically in wine or is it limited to me manually running the program?:P


Thanks!

---

### Post by CharlesA on 2011-01-10
As far as I know, you'd have to run the file for it to execute. I don't recall if there is an "autorun" feature in Wine or not.

In any case, even if you got a bug inside Wine, it would be confined to ~/.wine

---

### Post by marin123 on 2011-01-10
i had some kind of virus in wine that was sitting in my notification area all the time. so i guess its possible.

---

### Post by DanneStrat on 2011-01-10
Thank you for your replies!

"As far as I know, you'd have to run the file for it to execute. I don't recall if there is an "autorun" feature in Wine or not.

In any case, even if you got a bug inside Wine, it would be confined to ~/.wine"

OK, that's what I thought.

Thanks again.

I'm marking the thread solved.:)

---

### Post by bodhi.zazen on 2011-01-10
> **DanneStrat said:**
> Thank you for your replies!

"As far as I know, you'd have to run the file for it to execute. I don't recall if there is an "autorun" feature in Wine or not.

In any case, even if you got a bug inside Wine, it would be confined to ~/.wine"

OK, that's what I thought.

Thanks again.

I'm marking the thread solved.:)

It is possible for such an autorun virus to run in wine, it has been reported.

As long as you are NOT running wine as root, the virus would be confined to /home/your_user .

To confine wine to ~/.wine, remove the sym links in ~/.wine/dosdevices outside of ~/.wine or configure wine with winecfg

---

### Post by DanneStrat on 2011-01-11
> **bodhi.zazen said:**
> It is possible for such an autorun virus to run in wine, it has been reported.

As long as you are NOT running wine as root, the virus would be confined to /home/your_user .

To confine wine to ~/.wine, remove the sym links in ~/.wine/dosdevices outside of ~/.wine or configure wine with winecfg

I didn't know that. 

What would the steps be to confine wine to ~/.wine from inside the application? 

In what ways would it affect my installed applications?

---

### Post by CharlesA on 2011-01-11
I didn't know that either.

I'd go with winecfg, but I'm sure you could remove those symlinks manually fairly easily.

---

### Post by bodhi.zazen on 2011-01-11
> **DanneStrat said:**
> I didn't know that. 

What would the steps be to confine wine to ~/.wine from inside the application? 

In what ways would it affect my installed applications?

It will not affect your Linux installation as long as you are not running wine as root.

Do you know how to remove a symlink ?

```
cd ~/.wine/dosdevices
unlink ./*
```

Be sure to understand that as you may need to manually create links in the future to say your CDROM if you want to install applications.

I am not sure where the option is in winecfg (winecfg is a graphical configuration tool for wine).

---

### Post by movieman on 2011-01-11
Winecfg lets you configure virtual drives to point to your Linux files: by default Wine can access your entire disk, so I changed that to only allow it to access $HOME/Documents/Windows, which ensures any virus will only be able to write to that directory unless it can exploit a security hole in Wine itself. You can also put symbolic links to other directories in there, if you need to give Wine programs access to them without giving it access to your entire home directory or disk.

---

### Post by DanneStrat on 2011-01-11
"Be sure to understand that as you may need to manually create links in the future to say your CDROM if you want to install applications."

You mean when I want access to a CDROM from inside wine?

---

### Post by DanneStrat on 2011-01-11
"Be sure to understand that as you may need to manually create links in the future to say your CDROM if you want to install applications."

You mean when I want access to a CDROM from inside wine?

---

### Post by alphaamanitin on 2011-01-11
Could a windows virus running in wine, even if it was left to run rampant in a unconfined wine install ran as root, actually do anything to the linux system?  I mean, the file systems are totally different, aren't they?

AlphaA

---

### Post by DanneStrat on 2011-01-11
> **alphaamanitin said:**
> Could a windows virus running in wine, even if it was left to run rampant in a unconfined wine install ran as root, actually do anything to the linux system?  I mean, the file systems are totally different, aren't they?

AlphaA

In a default install of wine, all your documents and pictures etc.

would be accessible from inside wine.

So a virus could do anything to those files,

depending on what the current users permissions are.

---

### Post by bodhi.zazen on 2011-01-11
> **alphaamanitin said:**
> Could a windows virus running in wine, even if it was left to run rampant in a unconfined wine install ran as root, actually do anything to the linux system?  I mean, the file systems are totally different, aren't they?

AlphaA

> **DanneStrat said:**
> A default installation of wine maps the underlying filesystem to a fake C: drive, 
so that you have access to your files from inside wine. 
That means if a virus is runnng in wine it could modify all the files that the user has rights to modify.

And if you are running wine as root it can potentially modify system files.

When the rare virus that runs with wine is reported typically most every file in $HOME is affected (depending on symlinks outside of ~/.wine).

If there are no symlinks outside of ~/.wine, then only ~/.wine is affected.

So while "normally" windows viruses do not affect Linux, the can be "enabled" to run via wine.

---

### Post by alphaamanitin on 2011-01-11
> **bodhi.zazen said:**
> And if you are running wine as root it can potentially modify system files.

When the rare virus that runs with wine is reported typically most every file in $HOME is affected (depending on symlinks outside of ~/.wine).

If there are no symlinks outside of ~/.wine, then only ~/.wine is affected.

So while "normally" windows viruses do not affect Linux, the can be "enabled" to run via wine.


Hmm, how does the virus know how to deal with the linux file paths?  Please give an analogy as I couldn't follow the true technical way.  On second thought, even that might not work as I don't know exactly how wine works.  Does it make windows formatted symbolic links to your linux system?

AlphaA

---

### Post by bodhi.zazen on 2011-01-11
> **alphaamanitin said:**
> Hmm, how does the virus know how to deal with the linux file paths?  Please give an analogy as I couldn't follow the true technical way.  On second thought, even that might not work as I don't know exactly how wine works.  Does it make windows formatted symbolic links to your linux system?

AlphaA

As I said before, it uses Wine.

In wine, various directories are mapped to "virtual drives".

/ is mapped to z:\

Based on your question, you should look into how wine works if you are interested in the technical details.

---

### Post by DanneStrat on 2011-01-11
I've now removed the symlinks that point outside of ~./wine.

The only strange thing is that if i open wine notepad to try it out 

I can still see the / directory and all subdirectories. Why is that?

---

### Post by bodhi.zazen on 2011-01-11
> **DanneStrat said:**
> I've now removed the symlinks that point outside of ~./wine.

The only strange thing is that if i open wine notepad to try it out 

I can still see the / directory and all subdirectories. Why is that?

"see the / directory" where and how ?

This is what is strange about wine, it is running on Linux. Wine is a compaitibility layer, so, windows .exe, and viruses, will use windows paths and files, ie C:\. Wine uses a symlink to link z:\ to / . To install an application, windows exe want to use d:\ , not /media/cdrom. So wine provides a link linking d:\ to /dev/cdrom =)

So, you, as a user running linux will be able to access your files using linux paths.

You, as a user, will not be able to use Windows paths, ie c:\, unless you configure them.

Wine is a compatibility layer, not a security layer. We are simply disabling access by windows .exe or viruses to use z:\ to access / (and other windows paths).

If you want to add security, you could configure an apparmor profile to do so.

---

### Post by DanneStrat on 2011-01-12
Thanks for your help!

Thread solved.

---

