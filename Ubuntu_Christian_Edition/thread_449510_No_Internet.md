---
title: "No Internet"
date: 2007-05-20
forum: Ubuntu Christian Edition
---

### Post by deantn on 2007-05-20
Running a dual boot system with XP and Ubuntu7.04 everything works just fine connecting to internet but after 
'converting to CE can't get onto internet at all.
          Have tried all the posts instructions with no luck at all. Reinstalling everything and editing everything that was suggested.The network page comes up grayed out so I can't change anything on that page.And is stuck on "direct connect"
Don't know if being on satellite has anything to do with it  or not but I can get to internet with Fiesty with out CE being installed but add CE and no internet.
  Is there a way to disable Dansguardian so I can still use CE and get on internet, or am I just missing something? Being a newbie to Linux some of the terminology I am still learning about. Be willing to try just about anything that is suggested to fix this slight problem. Thanks in advance.:-({|=

---

### Post by mhancoc7 on 2007-05-20
> **deantn said:**
> Running a dual boot system with XP and Ubuntu7.04 everything works just fine connecting to internet but after 
'converting to CE can't get onto internet at all.
          Have tried all the posts instructions with no luck at all. Reinstalling everything and editing everything that was suggested.The network page comes up grayed out so I can't change anything on that page.And is stuck on "direct connect"
Don't know if being on satellite has anything to do with it  or not but I can get to internet with Fiesty with out CE being installed but add CE and no internet.
  Is there a way to disable Dansguardian so I can still use CE and get on internet, or am I just missing something? Being a newbie to Linux some of the terminology I am still learning about. Be willing to try just about anything that is suggested to fix this slight problem. Thanks in advance.:-({|=

Sounds like it may be an issue with the proxy settings. You can use the Ubuntu CE Parental Controls GUI. It is located here, System>Administration>Configure Parental Controls on the main menu. The GUI lets you Enable/Disable filtering, Lock/Unlock Firefox proxy settings, and tweak the filtering to your needs.

Hope that will help.

Jereme

---

### Post by deantn on 2007-05-21
> **mhancoc7 said:**
> Sounds like it may be an issue with the proxy settings. You can use the Ubuntu CE Parental Controls GUI. It is located here, System>Administration>Configure Parental Controls on the main menu. The GUI lets you Enable/Disable filtering, Lock/Unlock Firefox proxy settings, and tweak the filtering to your needs.

Hope that will help.

Jereme

Since I don't have "Configure Parental Controls" on the dropdown menu I conclude  that something is really wrong with my installation.
 Now how can I get back to just Ubnutu without formatting the Hdd, I've tried to reinstall CE but it tells me can't configure it.

---

### Post by mhancoc7 on 2007-05-21
> **deantn said:**
> Since I don't have "Configure Parental Controls" on the dropdown menu I conclude  that something is really wrong with my installation.
 Now how can I get back to just Ubnutu without formatting the Hdd, I've tried to reinstall CE but it tells me can't configure it.

What do you mean by, "it tells me can't configure it"?

You should be able to run the convert_me script again to correct the errors. Just be dure you are using the latest release of the script.

Give me a little more info and we should be able to get it resolved.

Jereme

---

### Post by deantn on 2007-05-21
DL the script again,while on XP. Loaded on to flash drive restarted and copied and pasted from flash drive to desktop.
Extracted to desktop,got this error; An Error Occurred While Extracting Files.
Looking at Command Line Output everything in there says at the end of each line;" Not Found in Archives" 
After that right clicked on "Convert Me" and after Password get this message" Ubuntu CE Convert Me script WILL NOT load because connection to the server could not be made. Try again later. Your default source.list will now be restored."

So obviously something wrong somewhere, can't get onto internet to get needed files in order to install CE.
Just would like to know how to get back to Ubuntu without CE. Rather have the CE but too much trouble to get installed over Ubuntu,bandwidth might be tight to try and DL the full version of CE but might try that way and see what happens. Unless there is an easy answer to this problem.
Thanks

---

### Post by mhancoc7 on 2007-05-21
> **deantn said:**
> DL the script again,while on XP. Loaded on to flash drive restarted and copied and pasted from flash drive to desktop.
Extracted to desktop,got this error; An Error Occurred While Extracting Files.
Looking at Command Line Output everything in there says at the end of each line;" Not Found in Archives" 
After that right clicked on "Convert Me" and after Password get this message" Ubuntu CE Convert Me script WILL NOT load because connection to the server could not be made. Try again later. Your default source.list will now be restored."

So obviously something wrong somewhere, can't get onto internet to get needed files in order to install CE.
Just would like to know how to get back to Ubuntu without CE. Rather have the CE but too much trouble to get installed over Ubuntu,bandwidth might be tight to try and DL the full version of CE but might try that way and see what happens. Unless there is an easy answer to this problem.
Thanks

Sorry, I should have thought of that. :)

Run the code below:

```
apt-get --purge remove --assume-yes dansguardian tinyproxy clamav firehol dansguardian-gui-ubuntu
```

Now download the attached archive. Extract it and open the "unlock_proxy" folder and double click the "unlock_proxy" file. Select "Run in Terminal".

Now reboot.

You may have to manually change your Firefox proxy settings to "Direct Connection".

You should now have the internet back with no filtering.

Let me know if you have any trouble.

Jereme

---

### Post by deantn on 2007-05-22
> 

Run the code below:

```
apt-get --purge remove --assume-yes dansguardian tinyproxy clamav firehol dansguardian-gui-ubuntu
```

Now download the attached archive. Extract it and open the "unlock_proxy" folder and double click the "unlock_proxy" file. Select "Run in Terminal".

Now reboot 

This is the answer I receive when I run the code

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
deantn@deantn:~$ 
How do I get to root to allow permissions,I am the only person on this computer so not sure why I am not allowed permission to the files in that directory.

---

### Post by tak1150 on 2007-05-22
In linux, there is a "root" user regardless of whether there is such a person or not. Important system things, by default, belong to that user.

To remedy your problem, you should type "sudo" before that same command

```
sudo apt-get --purge remove --assume-yes dansguardian tinyproxy clamav firehol dansguardian-gui-ubuntu
```

I hope that will help

---

### Post by mhancoc7 on 2007-05-22
Oops! Sorry, I forgot the sudo.

Jereme

---

### Post by deantn on 2007-05-22
Tried that and still no luck.
Gives me an answer about not finding things on server,24 errors as a matter of fact.
So I'll ask again how do I just get back to running Ubuntu with a fresh install or formatting HDD?](*,):-({|=

---

### Post by mhancoc7 on 2007-05-22
> **deantn said:**
> Tried that and still no luck.
Gives me an answer about not finding things on server,24 errors as a matter of fact.
So I'll ask again how do I just get back to running Ubuntu with a fresh install or formatting HDD?](*,):-({|=

I don't understand. You are getting server errors when trying to uninstall something. The code and script that I gave you should not depend on an internet connection. The code should completely remove dansguardian and the gui. The script should unlock your Firefox proxy settings. I have given these same instructions out before with no issue.

Please let me know exactly what you are doing in case I have missed something.

Jereme

---

### Post by deantn on 2007-05-25
Well after trying everything on this forum decided to format and just stick with Ubuntu without CE.Thanks for all the help anyway. As this was the second time I've tried to get CE with the same results both times thought I'm just not meant to have CE installed on this computer.

---

### Post by mhancoc7 on 2007-05-25
> **deantn said:**
> Well after trying everything on this forum decided to format and just stick with Ubuntu without CE.Thanks for all the help anyway. As this was the second time I've tried to get CE with the same results both times thought I'm just not meant to have CE installed on this computer.

Sorry that you never got it going. Did you ever try a fresh install of Ubuntu CE instead of using the convert_me script?

Jereme

---

### Post by deantn on 2007-05-25
> **mhancoc7 said:**
> Sorry that you never got it going. Did you ever try a fresh install of Ubuntu CE instead of using the convert_me script?

Jereme
No I haven't tried that yet but bandwidth right now at a premium so will have to wait until I have the bandwidth to do it and the time. Thanks anyway.
Learned a few more things about Linux and Ubuntu while trying to convert to CE, as a newbie to Linux command line is interesting. Not that hard to learn just trying to remember all the commands is getting a little easier as I go along.

---

### Post by mhancoc7 on 2007-05-25
> **deantn said:**
> No I haven't tried that yet but bandwidth right now at a premium so will have to wait until I have the bandwidth to do it and the time. Thanks anyway.
Learned a few more things about Linux and Ubuntu while trying to convert to CE, as a newbie to Linux command line is interesting. Not that hard to learn just trying to remember all the commands is getting a little easier as I go along.

Hey, I totally understand. I started with Ubuntu "Warty Warthog". I had NO linux experience. I remember having so many troubles. I was lost. I stuck with it though, and now I look back and I am amazed at how much I have learned. learning the "hard way" is the "best way" to learn. :)

Jereme

---

