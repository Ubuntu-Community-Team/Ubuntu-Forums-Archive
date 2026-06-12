---
title: "How to install Bitdefender, need help."
date: 2011-05-14
forum: Security
---

### Post by Christopher on 2011-05-14
I'm trying to install anti-virus Bitdefender on Ubuntu 11.04, file name is BitDefender-Antivirus-Scanner-7.6-4.linux gcc4x.amd64.deb.run  How do i get this to install? Thanks in advance. Chris.

---

### Post by wojox on 2011-05-14
```
chmod +x BitDefender-*
```

```
./Bitdefender-*
```

---

### Post by Christopher on 2011-05-14
> **wojox said:**
> ```
chmod +x BitDefender-*
```

```
./Bitdefender-*
```


I have it in a file on my desktop, should i change that?

---

### Post by wojox on 2011-05-14
> **Christopher said:**
> I have it in a file on my desktop, should i change that?

You could just

```
cd Desktop
```

---

### Post by sammiev on 2011-05-14
Heres's a [GREAT]("https://help.ubuntu.com/community/BitDefender") how-to. GL :)

---

### Post by Christopher on 2011-05-14
> **wojox said:**
> You could just

```
cd Desktop
```



Then like this?

christopher@christopher-132-CK-NF78:~/Desktop$ chmod +x BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run   ?

---

### Post by jtarin on 2011-05-14
You will need to be root to install.

---

### Post by Christopher on 2011-05-14
> **jtarin said:**
> You will need to be root to install.

Ok, thanks.

---

### Post by Christopher on 2011-05-15
Ok i acidently hid the system tray icon for Bitdefender, how do i get it back? I cant configure the anti-virus or how do i get rid of it lol.

---

### Post by ExileAmongYou on 2011-05-15
If you're running 11.04, just hit the super key/open the dash and start typing BitDefender, you should see it pop up as one of your installed applications (otherwise just look for it in the applications menu). Open it and change the settings from in there.

Are you trying to set it up to be always on? I have BitDefender installed but I don't leave it running in the background, I just do a scan every few weeks. You don't really need an always on virus scanner to the same extent in Linux.

---

### Post by Christopher on 2011-05-17
> **ExileAmongYou said:**
> If you're running 11.04, just hit the super key/open the dash and start typing BitDefender, you should see it pop up as one of your installed applications (otherwise just look for it in the applications menu). Open it and change the settings from in there.

Are you trying to set it up to be always on? I have BitDefender installed but I don't leave it running in the background, I just do a scan every few weeks. You don't really need an always on virus scanner to the same extent in Linux.

Ok thanks.

---

### Post by blennysalmon on 2011-09-22
Good step by step instructions [here:]("http://connectwww.com/how-to-install-bitdefender-antivirus-scanner-for-unices-on-ubuntu-11-04/1214/")

---

### Post by uRock on 2011-09-22
The best and safest way to install BitDefender is by using their repository. [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

### Post by TedinOz on 2011-11-30
> **blennysalmon said:**
> Good step by step instructions [here:]("http://connectwww.com/how-to-install-bitdefender-antivirus-scanner-for-unices-on-ubuntu-11-04/1214/")

I'm afraid I am a bit confused by this...it doesn't seem to work for me?

I downloaded text file to desktop and in running the commands given I get this result...

[HTML]ted@ted-Satellite-L300:~$ cd ~/Desktop
ted@ted-Satellite-L300:~/Desktop$ sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
[sudo] password for ted: 
sh: Can't open BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
ted@ted-Satellite-L300:~/Desktop$ 
[/HTML]

 It seems that I am unable to run a ‘sudo sh’ command. Is this a password issue? or should I be doing something to enable the use of ‘sudo sh’? I am relatively new to using the terminal so any advice would be appreciated. Thanks…

---

### Post by CharlesA on 2011-11-30
Just run this:

```
sudo ~/Desktop/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
```

No need to use sh.

---

### Post by TedinOz on 2011-11-30
> **CharlesA said:**
> Just run this:

```
sudo ~/Desktop/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
```

No need to use sh.

Thanks for your input but no go I'm afraid. Results here...

```
ted@ted-Satellite-L300:~$ cd ~/Desktop
ted@ted-Satellite-L300:~/Desktop$ sudo ~/Desktop/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
[sudo] password for ted: 
sudo: /home/ted/Desktop/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run: command not found
ted@ted-Satellite-L300:~/Desktop$ 

```

I'm now wondering that perhaps I have a bad download as it took a long time and kept timing out with a Google Chrome message saying that the page was not responding and giving me the choice to wait or kill. During that time my CPU was running at almost maximum. I just kept waiting until it came through and then saved to Desktop using right click and save. When I try to open the downloaded file I get this...
[IMG][[IMG]http://img841.imageshack.us/img841/7577/screenshotbitdefenderan.png[/IMG]](http://img841.imageshack.us/i/screenshotbitdefenderan.png/)[/IMG]

Any new thoughts?

---

### Post by CharlesA on 2011-11-30
It shouldn't be a text file. It's a binary file.

Try just right clicking and saving it that way.

---

### Post by sammiev on 2011-11-30
> **TedinOz said:**
> I'm afraid I am a bit confused by this...it doesn't seem to work for me?

I downloaded text file to desktop and in running the commands given I get this result...

[HTML]ted@ted-Satellite-L300:~$ cd ~/Desktop
ted@ted-Satellite-L300:~/Desktop$ sudo sh BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
[sudo] password for ted: 
sh: Can't open BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
ted@ted-Satellite-L300:~/Desktop$ 
[/HTML]

 It seems that I am unable to run a ‘sudo sh’ command. Is this a password issue? or should I be doing something to enable the use of ‘sudo sh’? I am relatively new to using the terminal so any advice would be appreciated. Thanks…

Try post #5 used it on many computers. :)

---

### Post by Paqman on 2011-11-30
> **uRock said:**
> The best and safest way to install BitDefender is by using their repository. [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

This.

In fact I would go further and say that installing it any other way is definitely not recommended. If you install apps outside the package manager they don't get updated, which is a big problem for a security-related app. If you use the repo the package will get automatically updated along with all other system updates.

---

### Post by sammiev on 2011-11-30
> **Paqman said:**
> This.

In fact I would go further and say that installing it any other way is definitely not recommended. If you install apps outside the package manager they don't get updated, which is a big problem for a security-related app. If you use the repo the package will get automatically updated along with all other system updates.

Exact same way as post #5. :)

---

### Post by TedinOz on 2011-11-30
> **CharlesA said:**
> It shouldn't be a text file. It's a binary file.

Try just right clicking and saving it that way.

No joy I'm afraid. When I right click the download page it is auto named as a .txt file and in Nautilus the only options available are to save as .txt or Allfiles. I tried Allfiles also with the same result. To right click the desktop file have no re-save options either.

@Paqman and sammiev, thank you both for your input also. On this link [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender), do I follow the link given for [http://connectwww.com/how-to-install-bitdefender-antivirus-scanner-for-unices-on-ubuntu-11-04/1214/comment-page-1/#comment-28749](http://connectwww.com/how-to-install-bitdefender-antivirus-scanner-for-unices-on-ubuntu-11-04/1214/comment-page-1/#comment-28749) or do I use the repository process described for 10.04 and Gnome? I am not running either of those and that's why I'm following the 11.04 option and that's what I am having trouble with.

---

### Post by CharlesA on 2011-11-30
Hrm.

Are you able to wget it?

```
wget http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
```

---

### Post by TedinOz on 2011-11-30
> **CharlesA said:**
> Hrm.

Are you able to wget it?

```
wget http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
```

I seem to have had success with your code. Output here...

```
ted@ted-Satellite-L300:~$ wget http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
--2011-12-01 14:33:12--  http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
Resolving download.bitdefender.com... 203.134.26.42, 203.134.26.43
Connecting to download.bitdefender.com|203.134.26.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41992207 (40M) [text/plain]
Saving to: 'BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run'

100%[======================================>] 41,992,207  1.38M/s   in 32s     

2011-12-01 14:33:44 (1.26 MB/s) - 'BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run' saved [41992207/41992207]

ted@ted-Satellite-L300:~$ 

```

Regrettably I admit that I don't know how to proceed from this point and any guidance will be greatly appreciated.

Thanks for your support :)

Edit: I have now found the newly saved file from wget in my home folder. Am I right in thinking that I now save this to desktop and proceed with installation as described?

---

### Post by dFlyer on 2011-11-30
Why waste your time installing a virus scanner not in the ubuntu archives. I've been using linux since the mid 90's and have never had a virus regardless of what distro I was running. My wife uses one from the archives and she hasn't had a virus either. I find virus scanners a waste of resources.

---

### Post by MartyBuntu on 2011-11-30
> **dFlyer said:**
> Why waste your time installing a virus scanner not in the ubuntu archives. I've been using linux since the mid 90's and have never had a virus regardless of what distro I was running. My wife uses one from the archives and she hasn't had a virus either. I find virus scanners a waste of resources.

I think it's a safe assumption the OP is aware of this and may possibly interested in protecting from cross-operating-system file infection.

---

### Post by sammiev on 2011-11-30
> **dFlyer said:**
> Why waste your time installing a virus scanner not in the ubuntu archives. I've been using linux since the mid 90's and have never had a virus regardless of what distro I was running. My wife uses one from the archives and she hasn't had a virus either. I find virus scanners a waste of resources.

You maybe correct sir. As long as I transfer files and other things to window OS computer I prefer to scan all items been moved. :)

---

### Post by uRock on 2011-11-30
I used the commands listed in [the link I posted earlier]("https://help.ubuntu.com/community/BitDefender"). It will install a GUI application, which should be present in the menus or with a quick search in Unity.

Please do not derail the thread. Folks are asking for help installing an app, lets help them.

---

### Post by beew on 2011-11-30
> **Paqman said:**
> This.

In fact I would go further and say that installing it any other way is definitely not recommended. If you install apps outside the package manager they don't get updated, which is a big problem for a security-related app. If you use the repo the package will get automatically updated along with all other system updates.

Normally I would agree, except that bittdefender's repo hasn't been updated since April 2010 so I don't think there is any difference how OP installs it. I think the viral definitions are being updated if you run update regularly from bd but the software itself hasn't been for a long time.

---

### Post by CharlesA on 2011-12-01
> **beew said:**
> Normally I would agree, except that bittdefender's repo hasn't been updated since April 2010 so I don't think there is any difference how OP installs it. I think the viral definitions are being updated if you run update regularly from bd but the software itself hasn't been for a long time.

Aye. I have a cronjob set to update the definitions every 3 hours (bit overkill, but eh..)

> **TedinOz said:**
> I seem to have had success with your code. Output here...

```
ted@ted-Satellite-L300:~$ wget http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
--2011-12-01 14:33:12--  http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
Resolving download.bitdefender.com... 203.134.26.42, 203.134.26.43
Connecting to download.bitdefender.com|203.134.26.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41992207 (40M) [text/plain]
Saving to: 'BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run'

100%[======================================>] 41,992,207  1.38M/s   in 32s     

2011-12-01 14:33:44 (1.26 MB/s) - 'BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run' saved [41992207/41992207]

ted@ted-Satellite-L300:~$ 

```

Regrettably I admit that I don't know how to proceed from this point and any guidance will be greatly appreciated.

Thanks for your support :)

Edit: I have now found the newly saved file from wget in my home folder. Am I right in thinking that I now save this to desktop and proceed with installation as described?

Awesome. You can just run it from your home directory then:

```
sudo ~/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
```

---

### Post by TedinOz on 2011-12-01
Happy now to say that by moving the wget file download to my desktop  the command installation worked flawlessly! I am still curious as to why the BitDefender file would only save as a .txt file but thanks to CharlesA, a way around this was found. Thanks also to all others who contributed and supported. 

@MartyBuntu, your explanation as to why I would like to have this is exactly right and confirms to me the goodwill of most posters on these forums. Once again the help has been great and today I have learnt more yet again!

Thanks to all! :)

---

### Post by CharlesA on 2011-12-01
Not sure why the browser thought it was a text file, maybe a hiccup or something. Glad you got it working. :)

---

