---
title: "Write allowed even APPARMOR forced in Firefox"
date: 2011-02-28
forum: Security
---

### Post by kapetr on 2011-02-28
Hello,

I use Ubuntu 10.10 with encrypted home. I'm new with apparmor.


My firefox-3.6.13 is now in enforce mode - with standard profile.
With this profile it should have write access only to:
owner @{HOME}/Downloads/* rw,

but I can save files (with standard downloadmanager of firefox) e.g. in $HOME itself and I can't find any other rule, which could allow that. I have thing, that ecryptfs  workaround just affects the eCryptFS "part of things" and limitations of normal filenames/paths (in mounted ecryptfs) are still possible.

----------------------------------------------------------------------------------------
So ... why can firefox write elsewhere as in to ${HOME}/Downloads ?
----------------------------------------------------------------------------------------

BTW: I get also this in kern.log (but not by saving a file as wrote above) :

Feb 27 05:49:30 duron650 kernel: [ 2284.886631] type=1400 audit(1298782170.190:48): apparmor="DENIED" operation="open" parent=1782 profile="/usr/lib/firefox-3.6.13/firefox-*bin" name="/home/.ecryptfs/hugo/.Private/ECRYPTFS_FNEK_ENCRYPTED.FWY1tHLaOszg1UQTPB2f1Zq7Xu0xztwk9hVX6-OCUaSGk2nU5ADkJx.rdk--/ECRYPTFS_FNEK_ENCRYPTED.FWY1tHLaOszg1UQTPB2f1Zq7Xu0xztwk9hVXFlmP1qlJBZ2eq7XFiWljUE--" pid=2209 comm="firefox-bin" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0

?? why do firefox try to write to it and why do it fail even with #13 workaround?

Feb 27 06:03:23 duron650 kernel: [ 3118.231818] type=1400 audit(1298783003.534:49): apparmor="DENIED" operation="open" parent=1782 profile="/usr/lib/firefox-3.6.13/firefox-*bin" name="/tmp/.X0-lock" pid=2304 comm="firefox-bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

?? Why try firefox to access X lock ?

Thanks for help

--kapetr

---

### Post by kapetr on 2011-02-28
So ... I have to sorry me - partially.

The write to all under $HOME is allowed by _/etc/apparmor.d/abstractions/ubuntu-browsers.d/user-files_: **owner @{HOME}/** w**

But ... in _/etc/apparmor.d/usr.bin.firefox_ is AFTER including the above this: 
> 
# Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,


Should this not again set access limits to the affected files/dirs ?
If not (?!) - how to disable it and then allow how I want ?

Maybe with **audit deny @{HOME}/** mrwkl** ?
But this construction is not described in _man apparmor.d_.
So ... how works redefining of rules in apparmors config files ?

--kapetr

---

### Post by rookcifer on 2011-02-28
> **kapetr said:**
> 
Maybe with **audit deny @{HOME}/** mrwkl** ?

No, you don't want to do that as it will only make it so that Firefox cannot access *anything* in /home at all.  Instead you will want to edit:

```
/etc/apparmor.d/abstractions/ubuntu-browsers.d/user-files
```

You will want to comment out a line like so:

```
@{HOME}/ r,
@{HOME}/** r,
**#owner @{HOME}/** w,**
owner @{HOME}/Desktop/** r,
```

Notice the hash.  This will comment out the line that allows Firefox to write to any /home location.  

Now your rules will be set by what is in the Firefox profile itself.  This means writing will only be allowed to ~/Downloads and ~/Desktop (or whatever other locations you specify in the Firefox profile itself).

---

### Post by kapetr on 2011-03-03
Hello,

this would be a possible solution, thank you.

But back to my question: how to change previously set rule (e.g. with #include) ? Should new (nearest to the end of processing) rule replace the previous ? Or just add more restriction - not make them softer ?  Or ... ? 

e.g.
owner @{HOME}/ rw,
owner @{HOME}/ r,

The result should be just "r", don't?
If not, then I have thing about the construct 

audit deny @{HOME}/** mrwkl

followed by new definition of rule - but due missing manual. I actually don't know, what is would make - so I better do not try it. 

Any ideas ?

--kapetr

---

### Post by rookcifer on 2011-03-03
There's no simple solution really.  If you deny write access to /home as I suggested earlier you will see that Firefox might not run properly since it needs to write to various files within /home (particularly .mozilla).  

I suppose the best way to go about it would be to do as I said earlier, but then watch your logs for any errors.  If the logs show Firefox needs to write to some files within /home, you can change the firefox profile itself to allow that.

All of these abstractions can be pretty confusing at times, I admit. If you really wanted to simplify things, you could create your profile from scratch and not use any abstractions, but that is a PITA and takes a lot of time.

P.S. I am not really sure I am understanding your question.  Your English has me a bit confused as to what exactly it is you're asking.  I hope I helped anyway, though.

---

