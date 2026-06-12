---
title: "update manager issues"
date: 2009-06-01
forum: System76 Support
---

### Post by miniyak on 2009-06-01
I just looked a little closer and it seems i really am having an issue with the update manager. About 5 seconds after i press check for new updates to refresh the update manager i asked for more details. in the narrow time frame status messages were available, i could see that most of whatever the update manager was looking for was failing to read. I repeated the process a couple times to get the screenshot

the photo upload here seems to want a URL... i just tried flicr and it blows. Does anyone have a suggestion for where i should host a 300mb screen shot?



*note* i started commenting about this issue here [http://ubuntuforums.org/showthread.php?t=1157205](http://ubuntuforums.org/showthread.php?t=1157205) but felt the problem deserved its own thread (being different from the OP's intentions and such...)

---

### Post by madverb on 2009-06-01
Try to do an update in terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by miniyak on 2009-06-01
terminal output=

miniyak@system76-pc:~$ sudo apt-get update
[sudo] password for miniyak: 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Hit [http://planet76.com](http://planet76.com) ./ Release.gpg
Ign [http://planet76.com](http://planet76.com) ./ Translation-en_US   
Hit [http://planet76.com](http://planet76.com) ./ Release             
Ign [http://planet76.com](http://planet76.com) ./ Packages
Hit [http://planet76.com](http://planet76.com) ./ Packages
Reading package lists... Done
miniyak@system76-pc:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       

Do "Hit" and "Ign" represent something significant?

---

### Post by thomasaaron on 2009-06-02
'Hit' means update manager successfully connected to the server. 'Ign' means that the server was, for whatever reason, ignored.

That's normal. You're output looks a lot like mine.

I'm not seeing the screenshot you mentioned. Try opening it with the gimp and scaling it down (in gimp: Image > Scale Image). This should help you drop it down to a more reasonable size.

---

### Post by miniyak on 2009-06-02
lol 300kb no mb.... i thought it was too big....for some reason uploading photos in firefox never works for me... but flock works... thats an other issue though, here is the screen shot

[IMG]http://viewmorepics.myspace.com/index.cfm?fuseaction=viewImage&friendID=427549422&albumID=1224843&imageID=13956162[/IMG]

*Edit* well, i was thinking the image would show up, i see only text though. I must be missing something?

---

### Post by miniyak on 2009-06-10
ok, scratch screenshots im not testing out every photo hosting service just to find the ubuntu forums are being less user friendly ubuntu its self, again.

I was figuring that the update manager would check for update on an actual time schedule but from what it looks like it only runs at start up(of a new session). I have only completely shut down 7-8 times since i have got the laptop. So, there seemed to be something wrong. After i shut down the other day and started a new session the update manager ran and seemed to work fine.

However there was nothing labeled s76 that came through. Would there be an indication that the s76 drivers are coming through ok?

---

### Post by thomasaaron on 2009-06-10
If you've run the restore functionality on your system76 driver, updates will come through. Right now, you should be running version 2.3.6. 

System76 drivers don't get updated all that often... once when there is a new release of Ubuntu, and maybe one or two or three times in between releases.

---

### Post by miniyak on 2009-06-10
im still on 2.3.5

---

### Post by thomasaaron on 2009-06-10
OK. Then you may want to try and install 2.3.6 manually. Here are instructions...

> The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager. 

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by miniyak on 2009-06-10
Everything seemed to work. Version number now displays 2.3.6 . Now its just a question of whether the update manager will take care of it next time. I'm going to say that this problem is solved for now. At least ill know what to do if it comes up again

Thanks everyone

---

