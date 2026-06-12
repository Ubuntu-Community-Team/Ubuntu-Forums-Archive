---
title: "Restricted shells"
date: 2009-03-24
forum: Security
---

### Post by bittis on 2009-03-24
Hi everyone,
i have a problem trying to decide how it is best to create a restricted shell.  What i want to achieve is a kiosk like environment where the user is restricted to a specific browser for example and a limited working environment.

A user should only be able to have access to a shell and run firefox but nothing else, either this is locally or remotely. 

I have seen people talk about restricted shells and i ve read about chroot and packages such as jailkit and a new project under the name lshell (although i have no idea how secure that is or how easy it would be to break out of it).  Is there something else out there that can help me achieve this in a way that it can be easily repeated and /or automated for many users?

Any feedback is apriciated

Thanks

---

### Post by bodhi.zazen on 2009-03-24
You are best off by far using apparmor.

See the sticky at the top of these forums and 

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

Specifically see jdong's jailbash profile.

You first :

sudo ln /bin/bash /usr/local/jailbash

Hard link ;)

Then apply the profile, modify it more if needed.

---

### Post by bittis on 2009-03-25
hey there,
thanks for the reply!  This seems more like an app restricting application rather than a jail shell kind of app, is this correct?  Or am i getting things wrong?

Thanks! :)

---

### Post by kevdog on 2009-03-25
Just a couple of ideas of what you may need:

MySecureShell: [http://translate.google.com/translate?u=http%3A%2F%2Fmysecureshell.sourceforge.net%2Ffr%2Findex.html&hl=fr&ie=UTF8&sl=fr&tl=en](http://translate.google.com/translate?u=http%3A%2F%2Fmysecureshell.sourceforge.net%2Ffr%2Findex.html&hl=fr&ie=UTF8&sl=fr&tl=en)

Jailkit: [http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

---

### Post by bodhi.zazen on 2009-03-25
> **bittis said:**
> hey there,
thanks for the reply!  This seems more like an app restricting application rather than a jail shell kind of app, is this correct?  Or am i getting things wrong?

Thanks! :)

I think you are getting the wrong impression of apparmor.

Yes, the most common use of apparmor is to restrict applications, however, to apparmor bash is just another application.

jailbash is easy to set up and quite effective. I suggest you take it for a test spin. If you need to modify the restrictions, the profile is easy to understand.

I think you will fine apparmor easy to configure and extremely effective.

---

### Post by bittis on 2009-03-26
Hey there, quick question regarding the following

sudo ln /bin/bash /usr/local/jailbash

wont this force all users to use jailbash?  If so is there a way of only forcing a few user accounts to use jailbash but not all?

---

### Post by bodhi.zazen on 2009-03-26
> **bittis said:**
> Hey there, quick question regarding the following

sudo ln /bin/bash /usr/local/jailbash

wont this force all users to use jailbash?  If so is there a way of only forcing a few user accounts to use jailbash but not all?

No, not at all.

You then add jailbash to your shells and set it as the log in shell.

You can eiter edit /etc/passwd or use (sudo) chsh user

The key is you are making a hard link and not a soft link.

---

### Post by bittis on 2009-03-27
> **bodhi.zazen said:**
> No, not at all.

You then add jailbash to your shells and set it as the log in shell.

You can eiter edit /etc/passwd or use (sudo) chsh user

The key is you are making a hard link and not a soft link.


I think this is starting to make more sense.  In other words if i want to limit what a user can do i can include all those restrictions in the jailbash profile.  

I was wondering how i could allow a user to start an application remotely via a freenx server, the user logging in would not need to have access to anything freenx needs in order to work, is this correct?  

When attempting to log in, freenx server, running under its own account would serve the user, giving him whatever he has access to, i.e. if he has access to run firefox, then all he would need is firefox paths and all to be included in his apparmor profile with apropriate access, as well as everything related to X, is this correct? or am i heading the wrong way here?

---

### Post by bodhi.zazen on 2009-03-27
I think you ar understanding what apparmor will do and the basics of what it does.

I do not understand what you are wanting to restrict access too.

If you give a user access to a desktop , that is access to a lot of things and there are a ton of applications in a desktop.

In addition there are some files in /etc a user needs to access such as /etc/passwd and /etc/groups.

I suggest you make a list of what you want to restrict access to, such as other users home directories and take a look at jailbash. jailbash restricts access to critical system files already while allowing a use access to a fairly standard set of apps. 

I think a better question to as is what is wrong with using jailbash ? Does it restrict somethign you need to allow or allow access to something you want to restrict ? Should be fairly easy to modify.

---

### Post by bittis on 2009-03-30
Hey there!
thank you for the reply.  I basically want to deny all access appart from what is needed to run firefox from freenx.  That will include access to jailbash too.  I will try and set jailbash to complain mode and see what it complains about i think

George

> **bodhi.zazen said:**
> I think you ar understanding what apparmor will do and the basics of what it does.

I do not understand what you are wanting to restrict access too.

If you give a user access to a desktop , that is access to a lot of things and there are a ton of applications in a desktop.

In addition there are some files in /etc a user needs to access such as /etc/passwd and /etc/groups.

I suggest you make a list of what you want to restrict access to, such as other users home directories and take a look at jailbash. jailbash restricts access to critical system files already while allowing a use access to a fairly standard set of apps. 

I think a better question to as is what is wrong with using jailbash ? Does it restrict somethign you need to allow or allow access to something you want to restrict ? Should be fairly easy to modify.

---

### Post by bittis on 2009-03-30
Actualy a followup on my own post, [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906), based on what is here, i am trying to create a profile for jailbash that will allow me to connect remotely to a host to run firefox via freenx.  Browsing the logs, it is not clear how using logprof would help update the jailbash profile.  There is no clear distinction between records.  Or Am i wrong saying this?



> **bittis said:**
> I think this is starting to make more sense.  In other words if i want to limit what a user can do i can include all those restrictions in the jailbash profile.  

I was wondering how i could allow a user to start an application remotely via a freenx server, the user logging in would not need to have access to anything freenx needs in order to work, is this correct?  

When attempting to log in, freenx server, running under its own account would serve the user, giving him whatever he has access to, i.e. if he has access to run firefox, then all he would need is firefox paths and all to be included in his apparmor profile with apropriate access, as well as everything related to X, is this correct? or am i heading the wrong way here?

---

### Post by bodhi.zazen on 2009-03-30
Not really sure what you are asking or what you are trying to confine.

FreeNX is basically sharing your desktop and X sessions and will likely be difficult to confine. Allowing access to Freenx is going to be huge and you are likely going to need to allow access to most of your system as that is what a desktop has access to.

What you are asking is IMO unrealistic.

If you just wish to forward FireFox, I suggest ssh

ssh -X

---

### Post by bittis on 2009-03-31
Hmm, i understand, what i thought would be possible to do is have freenx unrestricted, but only limit the access of the user on the system.  This is what i am trying to accomplish at the end of the day, give the user a restricted shell account through which i can enable access to firefox via X.

X forwarding would still require granting access for the user to X libraries and binaries and firefox, is this correct?

ssh with X forwarding would still require the same actions, right?

Btw i am having problems with profile creating and the @{HOME} variable.  Having  
  /@{HOME}/** r,
  /@{HOME}/* r,
  /@{HOME}/ r,

inside the rpofile doesn't allow a user to execute the ls command, inserting the actual path of the user though as so:
  /home/test/** r,
  /home/test/* r,
  /home/test/ r,

alows me to execute the ls command successfully.   

#include <tunables/global> 
is included in the profile so the variable @{HOME} is loaded.  Any ideas?

Thanks!

---

### Post by bodhi.zazen on 2009-03-31
I think your problem is with the initial / in "/@{HOME}

It should be just

@{HOME}/

and /* and /** is redundant 

so, just

@{HOME}/ r,
@{HOME}/** r,

---

### Post by bittis on 2009-03-31
ok, excellent! works now :)

I have another question regarding the apparmor project, is it still maintained by anyone?

---

### Post by bittis on 2009-03-31
actually i have another question regarding jailbash.

I am trying to create a profile for running firefox over x forwarding via jailbash, but i come at an error which i think might have to do with jailbash itself, perhaps.

bash: /usr/bin/firefox: /bin/sh: bad interpreter: Permission denied

Forgetting about firefox, does this look familiar to anyone?

---

### Post by bodhi.zazen on 2009-03-31
You probably need to modify your profile somewhat.

First - Is it working the way you want ? If so, do not change your profile.

If not, take a look at some sample profiles here : 

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

---

