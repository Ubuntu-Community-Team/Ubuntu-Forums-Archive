---
title: "Ubuntu CE Jaunty 64 bit: repository available"
date: 2009-07-20
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-07-20
I have just uploaded necessary packages for 64 bit. Now if you have 64 bit, you could add ubuntu ce. Please go to this link for instruction:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

Please help to test before we release iso for 64 bit.

DK

---

### Post by RevJack on 2009-07-20
I'll be happy to test it for you!

---

### Post by RevJack on 2009-07-20
After installing the 64-bit repository I get the following:

gpg: no valid OpenPGP data found.


Couldn't find package ubuntu-ce

---

### Post by david_kt on 2009-07-20
> **RevJack said:**
> After installing the 64-bit repository I get the following:

gpg: no valid OpenPGP data found.


Couldn't find package ubuntu-ce

I think there is some problem in the first post as I wrap the code. Please try again as follow, copy and past below to terminal:

Edit, sorry I could not make it appear properly, please go to this link for instruction:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)


DK

---

### Post by RevJack on 2009-07-20
I now have what appears to be a 64-bit UbuntuCE running! :)

---

### Post by david_kt on 2009-07-20
> **RevJack said:**
> I now have what appears to be a 64-bit UbuntuCE running! :)

Thank you for your feedback. Jereme would be very glad to learn that it is successfully tested. We might release the iso files soon, but may be I will wait until production release of 32 bit before releasing 64 bit.

DK

---

### Post by RevJack on 2009-07-20
Sounds good! So far, I have not run into any issues.

---

### Post by Caraibes on 2009-07-22
Looks like it's working... Good job !!!

Such a metapackage is very efficient, as folks don't "have to" install a new distro, but simply transform a "secular" Ubuntu into a CE...

---

### Post by mhancoc7 on 2009-07-22
> **david_kt said:**
> Thank you for your feedback. Jereme would be very glad to learn that it is successfully tested. We might release the iso files soon, but may be I will wait until production release of 32 bit before releasing 64 bit.

DK

Yes this is very good news!!

I would like to go ahead and release a 64 bit beta iso as soon as possible. This way we can send an announcement to Distrowatch. This will help in spreading the exposure a bit.

Thanks, Jereme

---

### Post by trulan on 2009-07-25
Thank you for all the work that went into this.  Successfully installed Ubuntu CE into Ubuntu Studio (64 bit).  So far so good!

---

### Post by mhancoc7 on 2009-07-26
> **trulan said:**
> thank you for all the work that went into this.  Successfully installed ubuntu ce into ubuntu studio (64 bit).  So far so good!

cool!

---

### Post by shane2peru on 2009-07-26
Hey this is great!!!  I will have to try it out too!!!  I will keep you posted.

Shane

---

### Post by shane2peru on 2009-07-28
David

That worked like a charm!!! I noticed the new repo works great!  I installed it on my laptop and desktop.  Both went very smoothly.  Thanks!

Shane

---

### Post by david_kt on 2009-07-28
> **shane2peru said:**
> David

That worked like a charm!!! I noticed the new repo works great!  I installed it on my laptop and desktop.  Both went very smoothly.  Thanks!

Shane

The ubuntu logout sound has problem, as such I did some hack to make sure ubuntu ce logout sound is activated by default. You will not able to change it. If you notice, there is no logout sound  in ubuntu default install.

Where as for login sound, you have to activate ubuntu ce sound. I have made an update to make sure the login sound is also use (but could be change to other sound).  But I have not updated the repository yet.

DK

---

### Post by shane2peru on 2009-07-28
> **david_kt said:**
> The ubuntu logout sound has problem, as such I did some hack to make sure ubuntu ce logout sound is activated by default. You will not able to change it. If you notice, there is no logout sound  in ubuntu default install.

Where as for login sound, you have to activate ubuntu ce sound. I have made an update to make sure the login sound is also use (but could be change to other sound).  But I have not updated the repository yet.

DK

As for the sounds my computer refused to play the ogg files for logout sounds and login sounds.  Instead it gave me some horrendous sounding thing when I tried to test them.  I converted them to wav, and they seemed to work fine!  Odd.  You can convert them simple enough with:
```

sox file.ogg file.wav

```
They are slightly larger, but they work. :)  I don't know if this is a problem across the board, or just a fluke on my end, but wanted to let you know about it.

Shane

**EDIT:**  This is odd.  When I tried this and it didn't work, I was in **System -> Administration -> Login Window** selected Accessibility tab.  When I tested the off files, it didn't work.  When I went to the **System -> Preferences -> Sound** I tried the ogg file, it worked fine.  I'm still scratching my head.  Odd.  I guess there isn't really a problem, but that was odd.

---

### Post by david_kt on 2009-07-29
> **shane2peru said:**
> 
**EDIT:**  This is odd.  When I tried this and it didn't work, I was in **System -> Administration -> Login Window** selected Accessibility tab.  When I tested the off files, it didn't work.  When I went to the **System -> Preferences -> Sound** I tried the ogg file, it worked fine.  I'm still scratching my head.  Odd.  I guess there isn't really a problem, but that was odd.

Not sure about the difference of login windows tab and sound tab. But if you check carefully, I have created 2 file type for logout sound, one with ogg, and one with wav. The ogg would be played using normal system, and also when you check using system > preference > sound.

The hack one I use wav file as ogg file could not be played properly using aplay.

Whereas for login sound, there is only one type i.e. ogg, it should not be a problem.

Please let me know if you still face problem with the sound.

DK

---

### Post by brianfactors on 2009-07-29
```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
[sudo] password for []: 
OK
OK
--2009-07-29 14:27:55--  http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list
Resolving ubuntuce.com... 66.40.7.42
Connecting to ubuntuce.com|66.40.7.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 418 [text/plain]
Saving to: `/etc/apt/sources.list.d/ubuntuce.list'

100%[======================================>] 418         --.-K/s   in 0s      

2009-07-29 14:27:56 (18.5 MB/s) - `/etc/apt/sources.list.d/ubuntuce.list' saved [418/418]

Ign http://ubuntuce.com jaunty_i386/ Release.gpg
Ign http://ubuntuce.com jaunty_i386/ Translation-en_US                         
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://ubuntuce.com jaunty_i386/ Release                                   
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://ppa.launchpad.net jaunty Release                                    
Get:1 http://ubuntuce.com jaunty_i386/ Packages [2333B]                        
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://archive.ubuntu.com jaunty/main Sources                              
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://archive.ubuntu.com jaunty/restricted Sources                        
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US              
Hit http://ppa.launchpad.net jaunty/main Sources                               
Hit http://security.ubuntu.com jaunty-security/restricted Packages   
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/multiverse Sources    
Hit http://us.archive.ubuntu.com jaunty/main Packages                
Hit http://us.archive.ubuntu.com jaunty/restricted Packages          
Hit http://us.archive.ubuntu.com jaunty/restricted Sources           
Hit http://us.archive.ubuntu.com jaunty/main Sources                 
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources           
Hit http://wine.budgetdedicated.com jaunty Release                   
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Hit http://us.archive.ubuntu.com jaunty/universe Sources             
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://wine.budgetdedicated.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://wine.budgetdedicated.com jaunty/main Packages
Fetched 2333B in 1s (1668B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: opensong but it is not installable
             Depends: usplash-theme-ubuntu-ce but it is not installable
E: Broken packages
```

Well, I honestly don't know that I will be using opensong anyway. But I can't find a 64 bit versions to install, so I'm kinda lost. I tried using
```
dkpg -i --force architecture
```
Along with getlibs, but that was no good because I could't find the binary after I installed it.

I'm using ubuntu 9.04, 64 bit edition.

Anyone had similar problem? Help?

---

### Post by Caraibes on 2009-07-29
I am also on CE64... Open Song is installed... Just fine... I don't really use it neither (yet...), but there hasn't been any problem...

---

### Post by trulan on 2009-07-29
Open song definitely works on my setup, (64 bit Ubuntu Studio/CE).  And unless I am missing something, the code you ran is for i386, ie, 32 bit.

---

### Post by shane2peru on 2009-07-29
> **brianfactors said:**
> ```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty[COLOR="Red"]_i386[/COLOR].list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce
[sudo] password for []: 
OK
OK
--2009-07-29 14:27:55--  http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_i386.list
Resolving ubuntuce.com... 66.40.7.42
Connecting to ubuntuce.com|66.40.7.42|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 418 [text/plain]
Saving to: `/etc/apt/sources.list.d/ubuntuce.list'

100%[======================================>] 418         --.-K/s   in 0s      

2009-07-29 14:27:56 (18.5 MB/s) - `/etc/apt/sources.list.d/ubuntuce.list' saved [418/418]

Ign http://ubuntuce.com jaunty[COLOR="Red"]_i386[/COLOR]/ Release.gpg
Ign http://ubuntuce.com jaunty[COLOR="Red"]_i386[/COLOR]/ Translation-en_US                         
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Ign http://ubuntuce.com jaunty_i386/ Release                                   
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://ppa.launchpad.net jaunty Release                                    
Get:1 http://ubuntuce.com jaunty_[COLOR="Red"]i386[/COLOR]/ Packages [2333B]                        
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://archive.ubuntu.com jaunty/main Sources                              
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://archive.ubuntu.com jaunty/restricted Sources                        
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US              
Hit http://ppa.launchpad.net jaunty/main Sources                               
Hit http://security.ubuntu.com jaunty-security/restricted Packages   
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/multiverse Sources    
Hit http://us.archive.ubuntu.com jaunty/main Packages                
Hit http://us.archive.ubuntu.com jaunty/restricted Packages          
Hit http://us.archive.ubuntu.com jaunty/restricted Sources           
Hit http://us.archive.ubuntu.com jaunty/main Sources                 
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources           
Hit http://wine.budgetdedicated.com jaunty Release                   
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Hit http://us.archive.ubuntu.com jaunty/universe Sources             
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://wine.budgetdedicated.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://wine.budgetdedicated.com jaunty/main Packages
Fetched 2333B in 1s (1668B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-ce: Depends: opensong but it is not installable
             Depends: usplash-theme-ubuntu-ce but it is not installable
E: Broken packages
```

Well, I honestly don't know that I will be using opensong anyway. But I can't find a 64 bit versions to install, so I'm kinda lost. I tried using
```
dkpg -i --force architecture
```
Along with getlibs, but that was no good because I could't find the binary after I installed it.

I'm using ubuntu 9.04, 64 bit edition.

Anyone had similar problem? Help?

Hmm, you grabed the wrong command, and you have the i386 repo installed.  I highlighted it to make it visible in the quote above.  This is the command you need:
```

wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty_amd.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update && sudo apt-get install ubuntu-ce

```
However you are going to need to go in and remove the old repository, and you should do it before doing the above.

Go to, **System -> Administration -> Software Sources** go to the Third Party Software tab, and uncheck the ubuntu-ce one in there.  You can probably pretty safely delete the Ubuntu-CE one there.  Be careful not to delete other stuff, just un-check it if you are unsure, then run that line up above in  a terminal.

Shane

---

### Post by brianfactors on 2009-10-17
Thanks. CE seems to be installing just fine. It did warn me about the repo not being authenticated, but that's all cool.

Looking forward to this version. Thanks for all your help!

> < > Brian

---

