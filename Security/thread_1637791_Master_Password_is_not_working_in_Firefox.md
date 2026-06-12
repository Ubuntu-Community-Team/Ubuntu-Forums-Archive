---
title: "Master Password is not working in Firefox"
date: 2010-12-04
forum: Security
---

### Post by toolmania1 on 2010-12-04
My master password is not saving any passwords in Firefox.  I use this also in Windows XP, and all my passwords get saved.

Any ideas?

Furthermore, is this even a good idea to begin with?  Can the passwords be stolen easily?

---

### Post by Sylchat on 2010-12-05
Have you imported your firefox profile from Windows? or some of its files?

You may want to try creating a new profile (firefox -P) and see if the Master password is working.

A master password is a better idea than no password. You can enhance the security by choosing other options (Activate [_FIPS_]("https://developer.mozilla.org/en/NSS/FIPS_Mode_-_an_explanation") in prefs)

---

### Post by bodhi.zazen on 2010-12-05
> **toolmania1 said:**
> My master password is not saving any passwords in Firefox.  I use this also in Windows XP, and all my passwords get saved.

Any ideas?

Furthermore, is this even a good idea to begin with?  Can the passwords be stolen easily?

I store passwords for sensitive sites in keepassx, which is cross platform.

The password feature works in firefox in Ubuntu, do you have apparmor enabled ?

---

### Post by toolmania1 on 2010-12-05
I am not sure if I have app armor enabled.  I have SELinux enabled and UFW.

Is there a way to get the FIPS to not prompt for the master password every single time we go to a web site?  Or is it building up the storage of passwords and won't ask us every time after we build up our normal passwords.

In Windows XP, I would be prompted for the master password one time while I was logged onto the computer or logged into Firefox.  Then, for every site I went to, the password was already filled in.  Is that how it will work with FIPS?

---

### Post by uRock on 2010-12-05
When you unclick this box it still asks for a master password?

---

### Post by bodhi.zazen on 2010-12-06
> **toolmania1 said:**
> I am not sure if I have app armor enabled.  I have SELinux enabled and UFW.

Is there a way to get the FIPS to not prompt for the master password every single time we go to a web site?  Or is it building up the storage of passwords and won't ask us every time after we build up our normal passwords.

In Windows XP, I would be prompted for the master password one time while I was logged onto the computer or logged into Firefox.  Then, for every site I went to, the password was already filled in.  Is that how it will work with FIPS?

SELinux ?

---

### Post by Sylchat on 2010-12-06
> **toolmania1 said:**
> 
Is there a way to get the FIPS to not prompt for the master password every single time we go to a web site?  Or is it building up the storage of passwords and won't ask us every time after we build up our normal passwords.

In Windows XP, I would be prompted for the master password one time while I was logged onto the computer or logged into Firefox.  Then, for every site I went to, the password was already filled in.  Is that how it will work with FIPS?

The Master password is asked the first time you load an HTTPS page (even with no login/pass fields), or a page with a login and/or password field you've saved before (on a non-HTTPS page).
FIPS actually locks the use of your local Firefox certificates.
Without FIPS, you don't get prompted for HTTPS sites, but only for saved login/pass fields.

---

### Post by toolmania1 on 2010-12-06
Re:
"When you unclick this box it still asks for a master password?"

I think I left the Master Password field checked.  I can confirm later.

Re:
"sorry ....facing another problem, I just downloaded a 64 bit server. I was trying to install the Joomla on the var/www folder that I fixed; but I wont be granted permission.
Can someone help me as I am new to this .......my aim is to use the machine as a multi site host."

Is this in the correct post or did you need a different post.  This seems like it should be under a different topic.

Re:
"SELinux?"

Yes, I installed SELinux instead of App Armor.

Re:
"The Master password is asked the first time you load an HTTPS page (even with no login/pass fields), or a page with a login and/or password field you've saved before (on a non-HTTPS page).
FIPS actually locks the use of your local Firefox certificates.
Without FIPS, you don't get prompted for HTTPS sites, but only for saved login/pass fields."

Ok, thank you for the information.

---

### Post by toolmania1 on 2010-12-06
So, I made the changes for FIPS on my windows machine as noted in the post in this thread.  How can we confirm FIPS is set up correctly?  What should I see happen now?

---

### Post by Sylchat on 2010-12-07
> **toolmania1 said:**
> So, I made the changes for FIPS on my windows machine as noted in the post in this thread.  How can we confirm FIPS is set up correctly?  What should I see happen now?

1. restart firefox, 
2. load an https page with no login
3. you should be prompted for a Master password

You would have more info here:
[https://developer.mozilla.org/en/NSS/FIPS_Mode_-_an_explanation](https://developer.mozilla.org/en/NSS/FIPS_Mode_-_an_explanation)

---

### Post by toolmania1 on 2010-12-07
Just to confirm, since one of the posts above made me unsure of this, am I to still have Master Password selected under Tools in Firefox?

---

### Post by Sylchat on 2010-12-07
> **toolmania1 said:**
> Just to confirm, since one of the posts above made me unsure of this, am I to still have Master Password selected under Tools in Firefox?

You can't have FIPS without a Master pass, if that's what you mean.

---

### Post by toolmania1 on 2010-12-07
Yes I do, thank you :-)

---

### Post by Valkyr333 on 2010-12-15
I'm having the same problem. If by "SELinux" you mean Linux Ubuntu: Satanic Edition, then we're right in the same vein here. Sorry if I misunderstand, but that's what I'm running and "SELinux" is something I've seen in various places in my system.

Anyways, I've tried unchecking "save passwords" and "use master password" (deleting my master password), restarting Firefox and setting it up again, but the same problem occurs. Odd thing is, my Master Password is requested and it all works fine on, for instance, the Personas page for the popular Firefox Add-On. However it never asks for my password on Facebook, Myspace, YouTube or several other sites. Any ideas?

---

### Post by uRock on 2010-12-15
> **Valkyr333 said:**
> I'm having the same problem. If by "SELinux" you mean Linux Ubuntu: Satanic Edition, then we're right in the same vein here. Sorry if I misunderstand, but that's what I'm running and "SELinux" is something I've seen in various places in my system.
SELinux is a security algorithm that helps protect the system. I haven't even started to work with it yet, but plan to in the near future. There should only be one package installed on the system by default. Here is the link to the [SELinux wiki]("http://en.wikipedia.org/wiki/Security-Enhanced_Linux") for more information on the application.

---

### Post by Sylchat on 2010-12-15
> **Valkyr333 said:**
> I'm having the same problem. If by "SELinux" you mean Linux Ubuntu: Satanic Edition, then we're right in the same vein here. 

OMG... didn't know this version :twisted:

---

### Post by toolmania1 on 2011-01-06
Well, this seemed to work.  Although, I do not have every step.  I set up FIPS ( just google FIPS with Firefox ).  Then, I was prompted for a Master Password.  Not sure why I had to set up FIPS.  

It may also have started working when I unchecked Master Password, rebooted, and then rechecked it.  Not sure of the exact method, but one of those seemed to get it to work.

---

