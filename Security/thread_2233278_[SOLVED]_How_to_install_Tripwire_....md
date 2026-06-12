---
title: "[SOLVED] How to install Tripwire ..."
date: 2014-07-07
forum: Security
---

### Post by patrikmellq on 2014-07-07
Hello, i want to learn and install Tripwire.
 I have made a fresh installation with Ubuntu 12.04 LTS with out internet connection.
 That is the point, making a fresh installation with out internet connection, so i know the install is fresh with no strange files or intrusion.

 Now i download Tripwire-2.4.2.2-scr.tar.bz2 from [http://sourceforge.net/projects/tripwire/?source=directory](http://sourceforge.net/projects/tripwire/?source=directory)

 Now i want to extract the file and run the .sh file to install Tripwire.
 But where should i extract the file?
 Should i just extract it in my home folder or should i create a folder where i extract Tripwire?

 This is my first question.

 Note for does who does not know what Tripwire is:
 Tripwire is a security system that indentify all your existing files on your operating system and give them a unique key or alghoritm.
 So if some one make an intrusion and modifi any file on your system, then Tripwire will notice this change.
 That means that Tripwire does not prevent one intrusion, but it make sure you will notice if it happens.
 Then you can see when and how the intrusion happend.
 So you don't need running root kits or any other kind of security software.

 Why would i need Tripwire!

 Well i am a fahter with my 11 year old kid, we change our family computer from Windows 8 to Ubuntu 12.04 LTS.
 On our family computer we store private fotograhpics, musik and other thins like paying bills on internet and so on.
 So i want to make sure that i get notice when or if i get one intrusion and Tripwire does that.

 I feel that a router and UFW is ok when it comes to security, but i need that extra to really feel secure.

---

### Post by Gyokuro on 2014-07-07
Hi

Is there any special reason why you want to use the source package and compile it instead to use the packaged Ubuntu release? Another thing is tripwire is a good but complicated tool but as as I read your message I think it's somehow an overkill and it is not something you set up in 10 minutes as you have continuous monitoring it and where do you save your tripwire database (usb stick, nfs share) and that's questions you should answer yourself. I could post you the commands and settings for a simple system but as I already wrote I think it's just an overkill. There is another possibility and which is much faster - if you want to be sure that nobody played with your files sha256sum all files and keep the checksums on usb sticks, full disk encryption for your system and a backup media and you are fairly safe - even in case those medias get stolen.

---

### Post by patrikmellq on 2014-07-07
Hello Gyokuro ...
Yes you right about my mistake using a src file - it was the only one i find at sourceforge - wrong by me.
Back to scratch with out being paranoid - maybe i can connect to internet with fresh installation ... what is the odds i will get intrusion at the same moment when i will install Tripwire :-)

Lets say i run:

sudo apt-get update
sudo apt-get install tripwire

Then it will first ask me to configure the mail application, do i want that?
What does it mean, is it here i tell tripwire where to send reports to my email?   
If i want to configure email notifications, i select "internet site" ... should i do that ...
Then what email should i enter in the empty field (my email adress?) <snip>

After that i better understand the way to install Tripwire.
I will enter the key phrases 

And after that comment out error messages by default with # signs 
Untill i get a clean database with 0 warnings or errors.

Then i have to read and practice some commands running and update Tripwire.

Now at the end i need to move the tripwire database to usb key (have no clue or idea about that or how it is done) ...

Cheers

---

### Post by patrikmellq on 2014-07-08
Here is some image i took from the beginning of the installation, that part i am not so sure about.
Now i install Tripwire and it was easy.
But i not sure i did the mail configuration correct.

This window ask if i want email configuration and i say yes.

[IMG]http://i60.tinypic.com/1zn24jm.png[/IMG]

Next window ask what kind of configuration i would like and i pick Internet.

[IMG]http://i57.tinypic.com/11rbzx2.png[/IMG]

Now last window want me to write email adress or at least i think so, i am not sure about this part.
But i understand it as i should provide my email adress to the email configuration.
Is this correct?

[IMG]http://i59.tinypic.com/xdsd4j.png[/IMG]

---

### Post by patrikmellq on 2014-07-08
Now i understand and find example on internet - when they say i should only post my emails domain name and it means hotmail.com in my case.
"Enter your mail domain name"

[IMG]http://i60.tinypic.com/2vwhce8.jpg[/IMG]

Now i can start to build a guide how to install Tripwire :-)

---

### Post by Gyokuro on 2014-07-08
Hi

Ok thanks for the screen shots. The tripwire policy is at: **/etc/tripwire/twpol.txt** and you should edit it and you delete following lines:

**/etc/rc.boot -> $(SEC_BIN);** ==> Ubuntu do not have it delete it our comment it out via put # in front of this line

**/proc -> $Device);** changes often and delete this line of comment it out
**/root** -> change it that it looks like following:

[B]# These files change the behavior of the root account
{
      rulename = "Root config files",
      severity = 100
}
{
    /root   -> $(SEC_CRIT); # Catch all additions to /root
    /root/.bashrc -> $(SEC_CONFIG);
}
[/B]
and then save your changes (I'm a vi/vim so use the editor of your choice) and after the update via twadmin your policy file:

**sudo twadmin -m P /etc/tripwire/twpol.txt**

and now you can initialize the tripwire database:

**sudo tripwire -m i**

and now you can copy the tripwire database on an USB stick and set the write protection bit and change the** /etc/tripwire/twcfg.txt** file to point to the new location. 

You have to re-create the encrypted tripwire configuration file:

**sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt**

copy the tripwire database on your USB stick and the final step:

if I have not forgotten something you can check your system:

**sudo tripwire --check**

- HTH

---

### Post by patrikmellq on 2014-07-09
> and then save your changes (I'm a vi/vim so use the editor of your choice

Thanks Gyokuro.
I am a beginner and will use vim as you suggest, but i don't like black screen so i will intall it with gui.

**I find a code to install vim with gui:**

sudo apt-get install vim vim-scripts vim-doc vim-latexsuite vim-gui-common vim-gtk

Then to run the vim with gui i write **gvim** in the terminal.

[IMG]http://i59.tinypic.com/24oyk93.png[/IMG]

---

### Post by patrikmellq on 2014-07-09
Can you tell me again what files i should comment out with # signs...
This is how my file looks like:

```

   

 # 
 # Standard Debian Tripwire configuration 
 # 
 # 
 # This configuration covers the contents of all 'Essential: yes' 
 # packages along with any packages necessary for access to an internet 
 # or system availability, e.g. name services, mail services, PCMCIA 
 # support, RAID support, and backup/restore support. 
 # 
  
 # 
 # Global Variable Definitions 
 # 
 # These definitions override those in to configuration file.  Do not          
 # change them unless you understand what you're doing. 
 # 
  
 @@section GLOBAL 
 TWBIN = /usr/sbin; 
 TWETC = /etc/tripwire; 
 TWVAR = /var/lib/tripwire; 
  
 # 
 # File System Definitions 
 # 
 @@section FS 
  
 # 
 # First, some variables to make configuration easier 
 # 
 SEC_CRIT      = $(IgnoreNone)-SHa ; # Critical files that cannot change 
  
 SEC_BIN       = $(ReadOnly) ;        # Binaries that should not change 
  
 SEC_CONFIG    = $(Dynamic) ;         # Config files that are changed 
 		        # infrequently but accessed 
 		        # often 
  
 SEC_LOG       = $(Growing) ;         # Files that grow, but that 
 			             # should never change ownership 
  
 SEC_INVARIANT = +tpug ;              # Directories that should never 
 		        # change permission or ownership 
  
 SIG_LOW       = 33 ;                 # Non-critical files that are of 
 				     # minimal security impact 
  
 SIG_MED       = 66 ;                 # Non-critical files that are of 
 				     # significant security impact 
  
 SIG_HI        = 100 ;                # Critical files that are 
 				     # significant points of 
 				     # vulnerability 
  
 # 
 # Tripwire Binaries 
 # 
 ( 
   rulename = "Tripwire Binaries", 
   severity = $(SIG_HI) 
 ) 
 { 
 	$(TWBIN)/siggen			-> $(SEC_BIN) ; 
 	$(TWBIN)/tripwire		-> $(SEC_BIN) ; 
 	$(TWBIN)/twadmin		-> $(SEC_BIN) ; 
 	$(TWBIN)/twprint		-> $(SEC_BIN) ; 
 } 
  
 # 
 # Tripwire Data Files - Configuration Files, Policy Files, Keys, 
 # Reports, Databases 
 # 
  
 # NOTE: We remove the inode attribute because when Tripwire creates a 
 # backup, it does so by renaming the old file and creating a new one 
 # (which will have a new inode number).  Inode is left turned on for 
 # keys, which shouldn't ever change. 
  
 # NOTE: The first integrity check triggers this rule and each 
 # integrity check afterward triggers this rule until a database update 
 # is run, since the database file does not exist before that point. 
 ( 
   rulename = "Tripwire Data Files", 
   severity = $(SIG_HI) 
 ) 
 { 
 	$(TWVAR)/$(HOSTNAME).twd	-> $(SEC_CONFIG) -i ; 
 	$(TWETC)/tw.pol			-> $(SEC_BIN) -i ; 
 	$(TWETC)/tw.cfg			-> $(SEC_BIN) -i ; 
 	$(TWETC)/$(HOSTNAME)-local.key	-> $(SEC_BIN) ; 
 	$(TWETC)/site.key		-> $(SEC_BIN) ; 
  
 	#don't scan the individual reports 
 	$(TWVAR)/report			-> $(SEC_CONFIG) (recurse=0) ; 
 } 
  
 # 
 # Critical System Boot Files 
 # These files are critical to a correct system boot. 
 # 
 ( 
   rulename = "Critical system boot files", 
   severity = $(SIG_HI) 
 ) 
 { 
 	/boot			-> $(SEC_CRIT) ; 
 	/lib/modules		-> $(SEC_CRIT) ; 
 } 
  
 ( 
   rulename = "Boot Scripts", 
   severity = $(SIG_HI) 
 ) 
 { 
 	/etc/init.d		-> $(SEC_BIN) ; 
 	/etc/rc.boot		-> $(SEC_BIN) ; 
 	/etc/rcS.d		-> $(SEC_BIN) ; 
 	/etc/rc0.d		-> $(SEC_BIN) ; 
 	/etc/rc1.d		-> $(SEC_BIN) ; 
 	/etc/rc2.d		-> $(SEC_BIN) ; 
 	/etc/rc3.d		-> $(SEC_BIN) ; 
 	/etc/rc4.d		-> $(SEC_BIN) ; 
 	/etc/rc5.d		-> $(SEC_BIN) ; 
 	/etc/rc6.d		-> $(SEC_BIN) ; 
 } 
  
  
 # 
 # Critical executables 
 # 
 ( 
   rulename = "Root file-system executables", 
   severity = $(SIG_HI) 
 ) 
 { 
 	/bin			-> $(SEC_BIN) ; 
 	/sbin			-> $(SEC_BIN) ; 
 } 
  
 # 
 # Critical Libraries 
 # 
 ( 
   rulename = "Root file-system libraries", 
   severity = $(SIG_HI) 
 ) 
 { 
 	/lib			-> $(SEC_BIN) ; 
 } 
  
  
 # 
 # Login and Privilege Raising Programs 
 # 
 ( 
   rulename = "Security Control", 
   severity = $(SIG_MED) 
 ) 
 { 
 	/etc/passwd		-> $(SEC_CONFIG) ; 
 	/etc/shadow		-> $(SEC_CONFIG) ; 
 } 
  
  
  
  
 # 
 # These files change every time the system boots 
 # 
 ( 
   rulename = "System boot changes", 
   severity = $(SIG_HI) 
 ) 
 { 
 	/var/lock		-> $(SEC_CONFIG) ; 
 	/var/run		-> $(SEC_CONFIG) ; # daemon PIDs 
 	/var/log		-> $(SEC_CONFIG) ; 
 } 
  
 # These files change the behavior of the root account 
 ( 
   rulename = "Root config files", 
   severity = 100 
 ) 
 { 
 	/root				-> $(SEC_CRIT) ; # Catch all additions to /root 
 	/root/mail			-> $(SEC_CONFIG) ; 
 	/root/Mail			-> $(SEC_CONFIG) ; 
 	/root/.xsession-errors		-> $(SEC_CONFIG) ; 
 	/root/.xauth			-> $(SEC_CONFIG) ; 
 	/root/.tcshrc			-> $(SEC_CONFIG) ; 
 	/root/.sawfish			-> $(SEC_CONFIG) ; 
 	/root/.pinerc			-> $(SEC_CONFIG) ; 
 	/root/.mc			-> $(SEC_CONFIG) ; 
 	/root/.gnome_private		-> $(SEC_CONFIG) ; 
 	/root/.gnome-desktop		-> $(SEC_CONFIG) ; 
 	/root/.gnome			-> $(SEC_CONFIG) ; 
 	/root/.esd_auth			-> $(SEC_CONFIG) ; 
 	/root/.elm			-> $(SEC_CONFIG) ; 
 	/root/.cshrc		        -> $(SEC_CONFIG) ; 
 	/root/.bashrc			-> $(SEC_CONFIG) ; 
 	/root/.bash_profile		-> $(SEC_CONFIG) ; 
 	/root/.bash_logout		-> $(SEC_CONFIG) ; 
 	/root/.bash_history		-> $(SEC_CONFIG) ; 
 	/root/.amandahosts		-> $(SEC_CONFIG) ; 
 	/root/.addressbook.lu		-> $(SEC_CONFIG) ; 
 	/root/.addressbook		-> $(SEC_CONFIG) ; 
 	/root/.Xresources		-> $(SEC_CONFIG) ; 
 	/root/.Xauthority		-> $(SEC_CONFIG) -i ; # Changes Inode number on login 
 	/root/.ICEauthority		    -> $(SEC_CONFIG) ; 
 } 
  
 # 
 # Critical devices 
 # 
 ( 
   rulename = "Devices & Kernel information", 
   severity = $(SIG_HI), 
 ) 
 { 
 	/dev		-> $(Device) ; 
 	/proc		-> $(Device) ; 
 } 
  
 # 
 # Other configuration files 
 # 
 ( 
   rulename = "Other configuration files", 
   severity = $(SIG_MED) 
 ) 
 { 
 	/etc		-> $(SEC_BIN) ; 
 } 
  
 # 
 # Binaries 
 # 
 ( 
   rulename = "Other binaries", 
   severity = $(SIG_MED) 
 ) 
 { 
 	/usr/local/sbin	-> $(SEC_BIN) ; 
 	/usr/local/bin	-> $(SEC_BIN) ; 
 	/usr/sbin	-> $(SEC_BIN) ; 
 	/usr/bin	-> $(SEC_BIN) ; 
 } 
  
 # 
 # Libraries 
 # 
 ( 
   rulename = "Other libraries", 
   severity = $(SIG_MED) 
 ) 
 { 
 	/usr/local/lib	-> $(SEC_BIN) ; 
 	/usr/lib	-> $(SEC_BIN) ; 
 } 
  
 # 
 # Commonly accessed directories that should remain static with regards 
 # to owner and group 
 # 
 ( 
   rulename = "Invariant Directories", 
   severity = $(SIG_MED) 
 ) 
 { 
 	/		-> $(SEC_INVARIANT) (recurse = 0) ; 
 	/home		-> $(SEC_INVARIANT) (recurse = 0) ; 
 	/tmp		-> $(SEC_INVARIANT) (recurse = 0) ; 
 	/usr		-> $(SEC_INVARIANT) (recurse = 0) ; 
 	/var		-> $(SEC_INVARIANT) (recurse = 0) ; 
 	/var/tmp	-> $(SEC_INVARIANT) (recurse = 0) ; 
 } 



```

---

### Post by Gyokuro on 2014-07-09
Hi

I have deleted all references which I have mentioned in my ugly howto and below a complete working tripwire configuration (you can diff your file with this one and you will find what I have delete, so you will learn to work with diff :-) and you start mastering GVIM, later vim and then comes the day when you will ask yourself why do I need a GUI ;-)

```
       

     # 
     # Standard Debian Tripwire configuration 
     # 
     # 
     # This configuration covers the contents of all 'Essential: yes' 
     # packages along with any packages necessary for access to an internet 
     # or system availability, e.g. name services, mail services, PCMCIA 
     # support, RAID support, and backup/restore support. 
     # 
      
     # 
     # Global Variable Definitions 
     # 
     # These definitions override those in to configuration file.  Do not          
     # change them unless you understand what you're doing. 
     # 
      
     @@section GLOBAL 
     TWBIN = /usr/sbin; 
     TWETC = /etc/tripwire; 
     TWVAR = /var/lib/tripwire; 
      
     # 
     # File System Definitions 
     # 
     @@section FS 
      
     # 
     # First, some variables to make configuration easier 
     # 
     SEC_CRIT      = $(IgnoreNone)-SHa ; # Critical files that cannot change 
      
     SEC_BIN       = $(ReadOnly) ;        # Binaries that should not change 
      
     SEC_CONFIG    = $(Dynamic) ;         # Config files that are changed 
     		        # infrequently but accessed 
     		        # often 
      
     SEC_LOG       = $(Growing) ;         # Files that grow, but that 
     			             # should never change ownership 
      
     SEC_INVARIANT = +tpug ;              # Directories that should never 
     		        # change permission or ownership 
      
     SIG_LOW       = 33 ;                 # Non-critical files that are of 
     				     # minimal security impact 
      
     SIG_MED       = 66 ;                 # Non-critical files that are of 
     				     # significant security impact 
      
     SIG_HI        = 100 ;                # Critical files that are 
     				     # significant points of 
     				     # vulnerability 
      
     # 
     # Tripwire Binaries 
     # 
     ( 
       rulename = "Tripwire Binaries", 
       severity = $(SIG_HI) 
     ) 
     { 
     	$(TWBIN)/siggen			-> $(SEC_BIN) ; 
     	$(TWBIN)/tripwire		-> $(SEC_BIN) ; 
     	$(TWBIN)/twadmin		-> $(SEC_BIN) ; 
     	$(TWBIN)/twprint		-> $(SEC_BIN) ; 
     } 
      
     # 
     # Tripwire Data Files - Configuration Files, Policy Files, Keys, 
     # Reports, Databases 
     # 
      
     # NOTE: We remove the inode attribute because when Tripwire creates a 
     # backup, it does so by renaming the old file and creating a new one 
     # (which will have a new inode number).  Inode is left turned on for 
     # keys, which shouldn't ever change. 
      
     # NOTE: The first integrity check triggers this rule and each 
     # integrity check afterward triggers this rule until a database update 
     # is run, since the database file does not exist before that point. 
     ( 
       rulename = "Tripwire Data Files", 
       severity = $(SIG_HI) 
     ) 
     { 
     	$(TWVAR)/$(HOSTNAME).twd	-> $(SEC_CONFIG) -i ; 
     	$(TWETC)/tw.pol			-> $(SEC_BIN) -i ; 
     	$(TWETC)/tw.cfg			-> $(SEC_BIN) -i ; 
     	$(TWETC)/$(HOSTNAME)-local.key	-> $(SEC_BIN) ; 
     	$(TWETC)/site.key		-> $(SEC_BIN) ; 
      
     	#don't scan the individual reports 
     	$(TWVAR)/report			-> $(SEC_CONFIG) (recurse=0) ; 
     } 
      
     # 
     # Critical System Boot Files 
     # These files are critical to a correct system boot. 
     # 
     ( 
       rulename = "Critical system boot files", 
       severity = $(SIG_HI) 
     ) 
     { 
     	/boot			-> $(SEC_CRIT) ; 
     	/lib/modules		-> $(SEC_CRIT) ; 
     } 
      
     ( 
       rulename = "Boot Scripts", 
       severity = $(SIG_HI) 
     ) 
     { 
     	/etc/init.d		-> $(SEC_BIN) ; 
      	/etc/rcS.d		-> $(SEC_BIN) ; 
     	/etc/rc0.d		-> $(SEC_BIN) ; 
     	/etc/rc1.d		-> $(SEC_BIN) ; 
     	/etc/rc2.d		-> $(SEC_BIN) ; 
     	/etc/rc3.d		-> $(SEC_BIN) ; 
     	/etc/rc4.d		-> $(SEC_BIN) ; 
     	/etc/rc5.d		-> $(SEC_BIN) ; 
     	/etc/rc6.d		-> $(SEC_BIN) ; 
     } 
      
      
     # 
     # Critical executables 
     # 
     ( 
       rulename = "Root file-system executables", 
       severity = $(SIG_HI) 
     ) 
     { 
     	/bin			-> $(SEC_BIN) ; 
     	/sbin			-> $(SEC_BIN) ; 
     } 
      
     # 
     # Critical Libraries 
     # 
     ( 
       rulename = "Root file-system libraries", 
       severity = $(SIG_HI) 
     ) 
     { 
     	/lib			-> $(SEC_BIN) ; 
     } 
      
      
     # 
     # Login and Privilege Raising Programs 
     # 
     ( 
       rulename = "Security Control", 
       severity = $(SIG_MED) 
     ) 
     { 
     	/etc/passwd		-> $(SEC_CONFIG) ; 
     	/etc/shadow		-> $(SEC_CONFIG) ; 
     } 
      
      
      
      
     # 
     # These files change every time the system boots 
     # 
     ( 
       rulename = "System boot changes", 
       severity = $(SIG_HI) 
     ) 
     { 
     	/var/lock		-> $(SEC_CONFIG) ; 
     	/var/run		-> $(SEC_CONFIG) ; # daemon PIDs 
     	/var/log		-> $(SEC_CONFIG) ; 
     } 
      
     # These files change the behavior of the root account 
     ( 
       rulename = "Root config files", 
       severity = 100 
     ) 
     { 
     	/root				-> $(SEC_CRIT) ; # Catch all additions to /root 
       	/root/.bashrc			-> $(SEC_CONFIG) ; 
     } 
      
     # 
     # Critical devices 
     # 
     ( 
       rulename = "Devices & Kernel information", 
       severity = $(SIG_HI), 
     ) 
     { 
     	/dev		-> $(Device) ; 
     } 
      
     # 
     # Other configuration files 
     # 
     ( 
       rulename = "Other configuration files", 
       severity = $(SIG_MED) 
     ) 
     { 
     	/etc		-> $(SEC_BIN) ; 
     } 
      
     # 
     # Binaries 
     # 
     ( 
       rulename = "Other binaries", 
       severity = $(SIG_MED) 
     ) 
     { 
     	/usr/local/sbin	-> $(SEC_BIN) ; 
     	/usr/local/bin	-> $(SEC_BIN) ; 
     	/usr/sbin	-> $(SEC_BIN) ; 
     	/usr/bin	-> $(SEC_BIN) ; 
     } 
      
     # 
     # Libraries 
     # 
     ( 
       rulename = "Other libraries", 
       severity = $(SIG_MED) 
     ) 
     { 
     	/usr/local/lib	-> $(SEC_BIN) ; 
     	/usr/lib	-> $(SEC_BIN) ; 
     } 
      
     # 
     # Commonly accessed directories that should remain static with regards 
     # to owner and group 
     # 
     ( 
       rulename = "Invariant Directories", 
       severity = $(SIG_MED) 
     ) 
     { 
     	/		-> $(SEC_INVARIANT) (recurse = 0) ; 
     	/home		-> $(SEC_INVARIANT) (recurse = 0) ; 
     	/tmp		-> $(SEC_INVARIANT) (recurse = 0) ; 
     	/usr		-> $(SEC_INVARIANT) (recurse = 0) ; 
     	/var		-> $(SEC_INVARIANT) (recurse = 0) ; 
     	/var/tmp	-> $(SEC_INVARIANT) (recurse = 0) ; 
     }
```

- HTH

---

### Post by patrikmellq on 2014-07-11
Hello Gyokuro and all ...

I understand i can compare my twpol.txt file with your twpol.txt file.
Do i comment out lines with # sign and then update twpol.txt file and after that create database?

Cheers

---

### Post by Gyokuro on 2014-07-11
Hi

Yes - you comment out everything with an in front # sign  and afterwards update your twpol.txt and recreate the database. 

OT: Thanks to the mods as it seems a brave soul put my posting in code tags - next time I do this myself - promised.

---

### Post by patrikmellq on 2014-07-12
> **Gyokuro said:**
> Hi

Yes - you comment out everything with an in front # sign  and afterwards update your twpol.txt and recreate the database. 

OT: Thanks to the mods as it seems a brave soul put my posting in code tags - next time I do this myself - promised.

Hello Gyokuro and all ...

Now there is one thing that bothers me with this picture.
When i install Tripwire i get error messages with things that not match and does i should remove with # sign with twpol.txt file.

But as you can see so can't i find any error messages with my twpol.txt file.
For example, if i have** /proc** then should it not say after that line **error no such file** and then i know i should comment out that part with **#** sign

Now i can only see what files i should remove if i compare my twpol.txt file with your twpol.txt file.


Cheers

---

### Post by Gyokuro on 2014-07-12
Hi

Ok I hope I get you correct - for example I have deleted the **/proc** line in my example post due to a lot of stuff changes in proc all the time and tripwire get noisy about all this changes. Some settings do not make any sense on Ubuntu due to they are not available or get handled different and you should change always one setting, test and make another change and retest again. However I do not know what you have already changed and I suggest that you repost your twpol.txt and in case of errors also the errors and I will take a look and fix whatever is wrong or do not make any sense. 

- HTH

---

### Post by patrikmellq on 2014-07-13
Hello Gyokuro and all ...
English is not my first languish so my writing can become fuzzy, but i will try again to explain.

There is a missunderstanding, i want to see wish files don't match.
Because my file has not been tailored for my system yet, so it should be a lot of warnings, false positives, and errors.

But i could not see them when opening twpol.txt.

Now i think i find a solution how to do this.
First a create twpol.txt file and after that the database.

Then i run a check and save the file as "test_results".
Now i should have a  list of files that are setting off tripwire with false postives and can  go through my policy file and edit it to get rid of these false  positives.
Now i can see them with the check file "test_results".

Now i open up twpol.txt and make changes.
Now i can search for each of the files that were returned in the "test_results" file and comment out all of the lines that i find match.

I will try this today and post the output files so you all can see how they look like.

---

### Post by patrikmellq on 2014-07-13
> **patrikmellq said:**
> Hello Gyokuro and all ...
English is not my first languish so my writing can become fuzzy, but i will try again to explain.

There is a missunderstanding, i want to see wish files don't match.
Because my file has not been tailored for my system yet, so it should be a lot of warnings, false positives, and errors.

But i could not see them when opening twpol.txt.

Now i think i find a solution how to do this.
First a create twpol.txt file and after that the database.

Then i run a check and save the file as "test_results".
Now i should have a  list of files that are setting off tripwire with false postives and can  go through my policy file and edit it to get rid of these false  positives.
Now i can see them with the check file "test_results".

Now i open up twpol.txt and make changes.
Now i can search for each of the files that were returned in the "test_results" file and comment out all of the lines that i find match.

I will try this today and post the output files so you all can see how they look like.

Now i test this and it works great, i got a file with all files that i should comment out.
 + there is some other tweaks you and others mention.
But now i get a raw "test_results" file that show me all the error messages and false positives.
That was what i was searching for.

:-)

This is how the file look like:

```

     Filename: /etc/rc.boot
     Filename: /root/mail
     Filename: /root/Mail
     Filename: /root/.xsession-errors
     Filename: /root/.xauth
     Filename: /root/.tcshrc
     Filename: /root/.sawfish
     Filename: /root/.pinerc
     Filename: /root/.mc
     Filename: /root/.gnome_private
     Filename: /root/.gnome-desktop
     Filename: /root/.gnome
     Filename: /root/.esd_auth
     Filename: /root/.elm
     Filename: /root/.cshrc
     Filename: /root/.bash_profile
     Filename: /root/.bash_logout
     Filename: /root/.bash_history
     Filename: /root/.amandahosts
     Filename: /root/.addressbook.lu
     Filename: /root/.addressbook
     Filename: /root/.Xresources
     Filename: /root/.Xauthority
     Filename: /root/.ICEauthority
     Filename: /proc/4116/fd/3
     Filename: /proc/4116/fdinfo/3
     Filename: /proc/4116/task/4116/fd/3
     Filename: /proc/4116/task/4116/fdinfo/3

```

---

### Post by Gyokuro on 2014-07-13
Hi

Ok thanks for the feedback - warning /etc/rc.boot => you can delete it as it's not available on Ubuntu, take a look at your /proc settings (if you delete/commented it out proc should not get reported).

- HTH

---

### Post by patrikmellq on 2014-07-13
Thanks Gyokuro ...
I find a guide on internet and it suggest how to remove /proc and modife /var ...
Very good guide ... [https://www.digitalocean.com/community/tutorials/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps)

I will try to complete this task and i am greatfull for your help Gyokuro.

Cheers

---

### Post by patrikmellq on 2014-07-13
Gyokuro i finally succed ... look at my new twpol.txt file ... i mark all lines with blue that i comment out with # sign and mark all added files with red.
And i use black screen with Nano editor :-)

I get no errors when i update twpol.txt file and database, now my tripwire system is clean and adjusted for my Ubuntu 12.04 LTS ...
Next i will fix so Tripwire send me one report each day to my email :-)

```


#
# Standard Debian Tripwire configuration
#
#
# This configuration covers the contents of all 'Essential: yes'
# packages along with any packages necessary for access to an internet
# or system availability, e.g. name services, mail services, PCMCIA
# support, RAID support, and backup/restore support.
#

#
# Global Variable Definitions
#
# These definitions override those in to configuration file.  Do not         
# change them unless you understand what you're doing.
#

@@section GLOBAL
TWBIN = /usr/sbin;
TWETC = /etc/tripwire;
TWVAR = /var/lib/tripwire;

#
# File System Definitions
#
@@section FS

#
# First, some variables to make configuration easier
#
SEC_CRIT      = $(IgnoreNone)-SHa ; # Critical files that cannot change

SEC_BIN       = $(ReadOnly) ;        # Binaries that should not change

SEC_CONFIG    = $(Dynamic) ;         # Config files that are changed
                # infrequently but accessed
                # often

SEC_LOG       = $(Growing) ;         # Files that grow, but that
                         # should never change ownership

SEC_INVARIANT = +tpug ;              # Directories that should never
                # change permission or ownership

SIG_LOW       = 33 ;                 # Non-critical files that are of
                     # minimal security impact

SIG_MED       = 66 ;                 # Non-critical files that are of
                     # significant security impact

SIG_HI        = 100 ;                # Critical files that are
                     # significant points of
                     # vulnerability

#
# Tripwire Binaries
#
(
  rulename = "Tripwire Binaries",
  severity = $(SIG_HI)
)
{
    $(TWBIN)/siggen            -> $(SEC_BIN) ;
    $(TWBIN)/tripwire        -> $(SEC_BIN) ;
    $(TWBIN)/twadmin        -> $(SEC_BIN) ;
    $(TWBIN)/twprint        -> $(SEC_BIN) ;
}

#
# Tripwire Data Files - Configuration Files, Policy Files, Keys,
# Reports, Databases
#

# NOTE: We remove the inode attribute because when Tripwire creates a
# backup, it does so by renaming the old file and creating a new one
# (which will have a new inode number).  Inode is left turned on for
# keys, which shouldn't ever change.

# NOTE: The first integrity check triggers this rule and each
# integrity check afterward triggers this rule until a database update
# is run, since the database file does not exist before that point.
(
  rulename = "Tripwire Data Files",
  severity = $(SIG_HI)
)
{
    $(TWVAR)/$(HOSTNAME).twd    -> $(SEC_CONFIG) -i ;
    $(TWETC)/tw.pol            -> $(SEC_BIN) -i ;
    $(TWETC)/tw.cfg            -> $(SEC_BIN) -i ;
    $(TWETC)/$(HOSTNAME)-local.key    -> $(SEC_BIN) ;
    $(TWETC)/site.key        -> $(SEC_BIN) ;

    #don't scan the individual reports
    $(TWVAR)/report            -> $(SEC_CONFIG) (recurse=0) ;
}

#
# Critical System Boot Files
# These files are critical to a correct system boot.
#
(
  rulename = "Critical system boot files",
  severity = $(SIG_HI)
)
{
    /boot            -> $(SEC_CRIT) ;
    /lib/modules        -> $(SEC_CRIT) ;
}

(
  rulename = "Boot Scripts",
  severity = $(SIG_HI)
)
{
    /etc/init.d        -> $(SEC_BIN) ;
    [COLOR=#0000ff]#/etc/rc.boot        -> $(SEC_BIN) ;[/COLOR]
    /etc/rcS.d        -> $(SEC_BIN) ;
    /etc/rc0.d        -> $(SEC_BIN) ;
    /etc/rc1.d        -> $(SEC_BIN) ;
    /etc/rc2.d        -> $(SEC_BIN) ;
    /etc/rc3.d        -> $(SEC_BIN) ;
    /etc/rc4.d        -> $(SEC_BIN) ;
    /etc/rc5.d        -> $(SEC_BIN) ;
    /etc/rc6.d        -> $(SEC_BIN) ;
}


#
# Critical executables
#
(
  rulename = "Root file-system executables",
  severity = $(SIG_HI)
)
{
    /bin            -> $(SEC_BIN) ;
    /sbin            -> $(SEC_BIN) ;
}

#
# Critical Libraries
#
(
  rulename = "Root file-system libraries",
  severity = $(SIG_HI)
)
{
    /lib            -> $(SEC_BIN) ;
}


#
# Login and Privilege Raising Programs
#
(
  rulename = "Security Control",
  severity = $(SIG_MED)
)
{
    /etc/passwd        -> $(SEC_CONFIG) ;
    /etc/shadow        -> $(SEC_CONFIG) ;
}




#
# These files change every time the system boots
#
(
  rulename = "System boot changes",
  severity = $(SIG_HI)
)
{
    [COLOR=#0000ff]#/var/lock        -> $(SEC_CONFIG) ;
    #/var/run        -> $(SEC_CONFIG) ; # daemon PIDs[/COLOR]
    /var/log        -> $(SEC_CONFIG) ;
}

# These files change the behavior of the root account
(
  rulename = "Root config files",
  severity = 100
)
{
    /root                -> $(SEC_CRIT) ; # Catch all additions to /root
    [COLOR=#0000ff]#/root/mail            -> $(SEC_CONFIG) ;
    #/root/Mail            -> $(SEC_CONFIG) ;
    #/root/.xsession-errors        -> $(SEC_CONFIG) ;
    #/root/.xauth            -> $(SEC_CONFIG) ;
    #/root/.tcshrc            -> $(SEC_CONFIG) ;
    #/root/.sawfish            -> $(SEC_CONFIG) ;
    #/root/.pinerc            -> $(SEC_CONFIG) ;
    #/root/.mc            -> $(SEC_CONFIG) ;
    #/root/.gnome_private        -> $(SEC_CONFIG) ;
    #/root/.gnome-desktop        -> $(SEC_CONFIG) ;
    #/root/.gnome            -> $(SEC_CONFIG) ;
    #/root/.esd_auth            -> $(SEC_CONFIG) ;
    #/root/.elm            -> $(SEC_CONFIG) ;
    #/root/.cshrc                -> $(SEC_CONFIG) ;
   [/COLOR][COLOR=#000000] /root/.bashrc            -> $(SEC_CONFIG) ;[/COLOR][COLOR=#0000ff]
    #/root/.bash_profile        -> $(SEC_CONFIG) ;
    #/root/.bash_logout        -> $(SEC_CONFIG) ;
    #/root/.bash_history        -> $(SEC_CONFIG) ;
    #/root/.amandahosts        -> $(SEC_CONFIG) ;
    #/root/.addressbook.lu        -> $(SEC_CONFIG) ;
    #/root/.addressbook        -> $(SEC_CONFIG) ;
    #/root/.Xresources        -> $(SEC_CONFIG) ;
    #/root/.Xauthority        -> $(SEC_CONFIG) -i ; # Changes Inode number on login
    #/root/.ICEauthority            -> $(SEC_CONFIG) ;[/COLOR]
}

#
# Critical devices
#
(
  rulename = "Devices & Kernel information",
  severity = $(SIG_HI),
)
{
    /dev        -> $(Device) ;
   [COLOR=#ff0000] /dev/pts    -> $(Device) ;[/COLOR]
   [COLOR=#0000ff] #/proc        -> $(Device) ;[/COLOR]
   [COLOR=#ff0000] /proc/devices    -> $(Device) ;
    /proc/net    -> $(Device) ;
    /proc/tty    -> $(Device) ;
    /proc/sys    -> $(Device) ;
    /proc/cpuinfo    -> $(Device) ;
    /proc/modules    -> $(Device) ;
    /proc/mounts    -> $(Device) ;
    /proc/dma    -> $(Device) ;
    /proc/filesystems -> $(Device) ;
    /proc/interrupts -> $(Device) ;
    /proc/ioports    -> $(Device) ;
    /proc/scsi    -> $(Device) ;
    /proc/kcore    -> $(Device) ;
    /proc/self    -> $(Device) ;
    /proc/kmsg    -> $(Device) ;
    /proc/stat    -> $(Device) ;
    /proc/loadavg    -> $(Device) ;
    /proc/uptime    -> $(Device) ;
    /proc/locks    -> $(Device) ;
    /proc/meminfo    -> $(Device) ;
    /proc/misc    -> $(Device) ;[/COLOR]
}

#
# Other configuration files
#
(
  rulename = "Other configuration files",
  severity = $(SIG_MED)
)
{
    /etc        -> $(SEC_BIN) ;
}

#
# Binaries
#
(
  rulename = "Other binaries",
  severity = $(SIG_MED)
)
{
    /usr/local/sbin    -> $(SEC_BIN) ;
    /usr/local/bin    -> $(SEC_BIN) ;
    /usr/sbin    -> $(SEC_BIN) ;
    /usr/bin    -> $(SEC_BIN) ;
}

#
# Libraries
#
(
  rulename = "Other libraries",
  severity = $(SIG_MED)
)
{
    /usr/local/lib    -> $(SEC_BIN) ;
    /usr/lib    -> $(SEC_BIN) ;
}

#
# Commonly accessed directories that should remain static with regards
# to owner and group
#
(
  rulename = "Invariant Directories",
  severity = $(SIG_MED)
)
{
    /        -> $(SEC_INVARIANT) (recurse = 0) ;
    /home        -> $(SEC_INVARIANT) (recurse = 0) ;
    /tmp        -> $(SEC_INVARIANT) (recurse = 0) ;
    /usr        -> $(SEC_INVARIANT) (recurse = 0) ;
    /var        -> $(SEC_INVARIANT) (recurse = 0) ;
    /var/tmp    -> $(SEC_INVARIANT) (recurse = 0) ;
}



```

---

### Post by patrikmellq on 2014-07-13
GyoKuro ...

I run ... sudo tripwire --check
And find 3 modified files at /etc ... not sure what this is ?
All files should show zero !!!

I have not install or update anything ... only tripwire ....


```

patrik@patrik-ubuntu:~$ sudo tripwire --check
[sudo] password for patrik: 
Parsing policy file: /etc/tripwire/tw.pol
*** Processing Unix File System ***
Performing integrity check...
Wrote report file: /var/lib/tripwire/report/patrik-ubuntu-20140713-202129.twr


Open Source Tripwire(R) 2.4.2.2 Integrity Check Report

Report generated by:          root
Report created on:            Sun Jul 13 20:21:29 2014
Database last updated on:     Never

===============================================================================
Report Summary:
===============================================================================

Host name:                    patrik-ubuntu
Host IP address:              127.0.1.1
Host ID:                      None
Policy file used:             /etc/tripwire/tw.pol
Configuration file used:      /etc/tripwire/tw.cfg
Database file used:           /var/lib/tripwire/patrik-ubuntu.twd
Command line used:            tripwire --check 

===============================================================================
Rule Summary: 
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

  Rule Name                       Severity Level    Added    Removed  Modified 
  ---------                       --------------    -----    -------  -------- 
  Other binaries                  66                0        0        0        
  Tripwire Binaries               100               0        0        0        
  Other libraries                 66                0        0        0        
  Root file-system executables    100               0        0        0        
  Tripwire Data Files             100               0        0        0        
  System boot changes             100               0        0        0        
  (/var/log)
  Root file-system libraries      100               0        0        0        
  (/lib)
  Critical system boot files      100               0        0        0        
* Other configuration files       66                0        0        3        
  (/etc)
  Boot Scripts                    100               0        0        0        
  Security Control                66                0        0        0        
  Root config files               100               0        0        0        
  Devices & Kernel information    100               0        0        0        
  Invariant Directories           66                0        0        0        

Total objects scanned:  27259
Total violations found:  3

===============================================================================
Object Summary: 
===============================================================================

-------------------------------------------------------------------------------
# Section: Unix File System
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
Rule Name: Other configuration files (/etc)
Severity Level: 66
-------------------------------------------------------------------------------

Modified:
"/etc/cups"
"/etc/cups/subscriptions.conf"
"/etc/cups/subscriptions.conf.O"

===============================================================================
Error Report: 
===============================================================================

No Errors

-------------------------------------------------------------------------------
*** End of report ***

Open Source Tripwire 2.4 Portions copyright 2000 Tripwire, Inc. Tripwire is a registered
trademark of Tripwire, Inc. This software comes with ABSOLUTELY NO WARRANTY;
for details use --version. This is free software which may be redistributed
or modified only under certain conditions; see COPYING for details.
All rights reserved.
Integrity check complete.
patrik@patrik-ubuntu:~$ 

```

---

### Post by Gyokuro on 2014-07-14
Hi

Glad that you got it working and it seems it works and no problem and here is some information what happened: Tripwire found changes in /etc/cups -> cups (**C**ommon **U**nix** P**rinting **S**ystem) and a possibility that something changed could be that during updates package scripts get triggered and the CUPS configuration get rebuilt/updated and as it's the system default printer service (it handles most of the printing stuff and a lot of applications are depending on the CUPS printer service - [https://launchpad.net/ubuntu/+source/cups](https://launchpad.net/ubuntu/+source/cups)) you can either ignore it or change your tripwire config so it excludes /etc/cups. However you should not forget that tripwire will check everything against it's database and over time with updates there are warnings that something changed - that's good and for this reason you have installed tripwire - to monitor your system files or whatever files you want to monitor - the mentioned files you should check and over time you will get a feeling what is important and what's are simple false alarms. 

- HTH

---

### Post by patrikmellq on 2014-07-14
Thanks Gyokuro ...
Now i need your help with one last thing - how to install database on usb stick so no one can change it.
What is the name of the database file? is it also located at /etc/tripwire folder?

I search internet, but could not find any guide for how to install Tripwire database on removable media.
Should i also save twpol.txt file on usb stick ?

I assume the commands will be different when the Tripwire database is on a usb stick.

Many thanks

Patrik

---

### Post by patrikmellq on 2014-07-14
Ops i made same post twice ...

---

### Post by Gyokuro on 2014-07-14
Hi Patrik

No problem - we are all humans and sometimes I write in Master Yoda English. Basically tripwire needs to know where the database is located and in /etc/tripwire/twcfg.txt you should change following part of the file that reads:

DBFILE =/var/lib/tripwire/$(HOSTNAME).twd

to

DBFILE =/mnt/usbstick/tripwire/$(HOSTNAME).twd 

means /mnt/usbstick is the directory where you mount your usbstick and in case you make an directory on you usbstick which I named in this example tripwire you have point in your /etc/tripwire/twcfg.txt to this mount point and directory (name the directoy something else - shoppinglist or whatever). After you have changed the location in your twcfg.txt you have to re-created the encrypted Tripwire configuration with:

sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt 

I suggest you that you copy the /etc/tripwire/site.key to another usb stick or whatever you want to use to store securely this key. After tripwire check runs you will find date-stamped files in /var/lib/tripwire/reports/ => copy this files also to a save place due to in case of an investigation you have a proof. Another thing is that you can check even single files:

sudo tripwire -m c /bin/ls

another thing you wrote is that you want to email the results to an email address you can test it whether it works via:

sudo tripwire --test -e [email]youremail@yourdomain.com[/email]

- HTH

---

### Post by patrikmellq on 2014-07-15
Hello Gyokuro and all ...

> Basically tripwire needs to know where the database is located and in  /etc/tripwire/twcfg.txt you should change following part of the file  that reads:

DBFILE =/var/lib/tripwire/$(HOSTNAME).twd

to

DBFILE =/mnt/usbstick/tripwire/$(HOSTNAME).twd

This part was easy and i open up nano and change the path.
After that i create a folder with the name "tripwire" on my usbstick.

Then after that i try to re-creat the encrypted Tripwire configuration with your code:
```

sudo twadmin -m -F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt

```

But it complain about the letter -F and will not run the code:

[IMG]http://i62.tinypic.com/xm3kw0.png[/IMG]

Cheers Patrik

---

### Post by Gyokuro on 2014-07-17
Hi

Sorry for the late response and I have fixed the command and should be:

sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt 

- HTH

---

### Post by patrikmellq on 2014-07-18
YES :-) the code work perfect - Thanks Gyokuro ...

Now the path is wrong for the usbstick ... it is located at "media" folder and the name of the usbstick is "887D-1ED9"
So what should the path be in the twcfg.txt file

Example: /mnt/media/887D-1ED9/tripwire/$(HOSTNAME).twd

I test the terminal and i reach the databse with that path

[IMG]http://i61.tinypic.com/2rc4chl.png[/IMG]

---

### Post by patrikmellq on 2014-07-18
LOL Gyokuro ... i fix it ... i solve the path ...
I remove /mnt as the usbstick mount automatically and just add following path:
```

/media/887D-1ED9/tripwire/$(HOSTNAME).twd

```

> I suggest you that you copy the /etc/tripwire/site.key to another usb  stick or whatever you want to use to store securely this key. After  tripwire check runs you will find date-stamped files in  /var/lib/tripwire/reports/ => copy this files also to a save place  due to in case of an investigation you have a proof.

[IMG]http://i57.tinypic.com/25h3884.png[/IMG]

So now if i want to change the path for the site.key and put it on my usbstick i wirte following in twcfg.txt:

```

/media/887D-1ED9/tripwire/site.key

```

And with report file i create a folder in tripwire folder witht the name report:

```

/media/887D-1ED9/tripwire/report//$(HOSTNAME) - $(DATE).twr

```

WOW i start to understand this fully and it feels great Gyokuro

---

### Post by patrikmellq on 2014-07-18
Gyokuro i remove the database file from /var/lib/tripwire because i wanted to see if Tripwire works using my usbstick with the database.

It does not work when i run sudo tripwire --check
It say warning no such file or direcotry
/var/lib/tripwire/partik-ubuntu.twd

So i am back from scratch again.
I am not sure what i am doing wrong.

After i change twcfg.txt file i update with your code.
Maybe it does not notice the change i made when re-configurate.

---

### Post by Gyokuro on 2014-07-18
Hi

You forgot something -  to tell tripwire the new location of your tripwire database where it is and therefore you have to re-create the encrypted tripwire configuration: 

sudo twadmin -m F -S /whereeveryouhavestoredthis/tripwire/site.key /whereeveryouhavestoredthis/tripwire/twcfg.txt 

basically tripwire do not care where your keys and database or reports directory are located as long you enter the path in it's configuration file (the configuration/database get both encrypted and tripwire checks whether someone played with your tripwire configuration/database). So in case you change something or begin with a complete new config/database:

1.) settings in twpol.txt 

     sudo twadmin -m P /whereveryoustoreyourtwpoltxt/tripwire/twpol.txt

2.) initialize your tripwire database (should be a snapshot of a fresh and already hardened system)

    sudo tripwire -m i

3.) Re-create the encrypted tripwire configuration (in case you forgot something, changed something) and you have to issue this command as soon something in your twcfg.txt got changed.

     sudo twadmin -m F -S /whereeveryouhavestoredthis/tripwire/site.key /whereeveryouhavestoredthis/tripwire/twcfg.txt

4.) Usual tripwire check

     sudo tripwire --check

- HTH

---

### Post by patrikmellq on 2014-07-18
.

Hello Gyokuro ... thanks for your patience with me.

I follow your guide and it works to run "sudo tripwire --check" in the end of all code.
I can also see that the tripwire report use the path   /media/887D-1ED9/tripwire/patrik-ubuntu.twd
But i still got the warning about /var/lib/tripwire/patrik-ubuntu.twd ,,, but after the warning it say "continuing" and i got my report.

You can see all the code and response below.

```

patrik@patrik-ubuntu:~$ sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt
[sudo] password for patrik: 
Please enter your site passphrase: 
Wrote configuration file: /etc/tripwire/tw.cfg
patrik@patrik-ubuntu:~$ sudo twadmin -m P /etc/tripwire/twpol.txt
Please enter your site passphrase: 
Wrote policy file: /etc/tripwire/tw.pol
patrik@patrik-ubuntu:~$ sudo tripwire -m i
Please enter your local passphrase: 
Parsing policy file: /etc/tripwire/tw.pol
Generating the database...
*** Processing Unix File System ***
### Warning: File system error.
### Filename: /var/lib/tripwire/patrik-ubuntu.twd
### No such file or directory
### Continuing...
Wrote database file: /media/887D-1ED9/tripwire/patrik-ubuntu.twd
The database was successfully generated.
patrik@patrik-ubuntu:~$ sudo twadmin -m F -S /etc/tripwire/site.key /etc/tripwire/twcfg.txt
Please enter your site passphrase: 
Wrote configuration file: /etc/tripwire/tw.cfg
patrik@patrik-ubuntu:~$ sudo tripwire --check
Parsing policy file: /etc/tripwire/tw.pol
*** Processing Unix File System ***
Performing integrity check...
### Warning: File system error.
### Filename: /var/lib/tripwire/patrik-ubuntu.twd
### No such file or directory
### Continuing...
Wrote report file: /var/lib/tripwire/report/patrik-ubuntu-20140718-231617.twr


Open Source Tripwire(R) 2.4.2.2 Integrity Check Report

Report generated by:          root
Report created on:            Fri Jul 18 23:16:17 2014
Database last updated on:     Never

===============================================================================
Report Summary:
===============================================================================

Host name:                    patrik-ubuntu
Host IP address:              127.0.1.1
Host ID:                      None
Policy file used:             /etc/tripwire/tw.pol
Configuration file used:      /etc/tripwire/tw.cfg
Database file used:           /media/887D-1ED9/tripwire/patrik-ubuntu.twd
Command line used:            tripwire --check 

===============================================================================
Rule Summary: 
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

  Rule Name                       Severity Level    Added    Removed  Modified 
  ---------                       --------------    -----    -------  -------- 
  Other binaries                  66                0        0        0        
  Tripwire Binaries               100               0        0        0        
  Other libraries                 66                0        0        0        
  Root file-system executables    100               0        0        0        
* Tripwire Data Files             100               0        0        1        
  System boot changes             100               0        0        0        
  (/var/log)
  Root file-system libraries      100               0        0        0        
  (/lib)
  Critical system boot files      100               0        0        0        
* Other configuration files       66                0        0        2        
  (/etc)
  Boot Scripts                    100               0        0        0        
  Security Control                66                0        0        0        
  Root config files               100               0        0        0        
  Devices & Kernel information    100               0        0        0        
  Invariant Directories           66                0        0        0        

Total objects scanned:  32688
Total violations found:  3

===============================================================================
Object Summary: 
===============================================================================

-------------------------------------------------------------------------------
# Section: Unix File System
-------------------------------------------------------------------------------

-------------------------------------------------------------------------------
Rule Name: Other configuration files (/etc)
Severity Level: 66
-------------------------------------------------------------------------------

Modified:
"/etc/tripwire"
"/etc/tripwire/tw.cfg.bak"

-------------------------------------------------------------------------------
Rule Name: Tripwire Data Files (/etc/tripwire/tw.cfg)
Severity Level: 100
-------------------------------------------------------------------------------

Modified:
"/etc/tripwire/tw.cfg"

===============================================================================
Error Report: 
===============================================================================

-------------------------------------------------------------------------------
  Section: Unix File System
-------------------------------------------------------------------------------

1.   File system error.
     Filename: /var/lib/tripwire/patrik-ubuntu.twd
     No such file or directory

-------------------------------------------------------------------------------
*** End of report ***

Open Source Tripwire 2.4 Portions copyright 2000 Tripwire, Inc. Tripwire is a registered
trademark of Tripwire, Inc. This software comes with ABSOLUTELY NO WARRANTY;
for details use --version. This is free software which may be redistributed
or modified only under certain conditions; see COPYING for details.
All rights reserved.
Integrity check complete.
patrik@patrik-ubuntu:~$ 


```

You can see at the report i get the error even if it works.
Can i comment out with # sign the /var/lib/tripwire with twpol.txt ... even if its not listed ... maybe i can add some code?
Or should i just ignore it ...

---

### Post by patrikmellq on 2014-07-19
.

A big thank you to you  Gyokuro for all your help.
You made me very happy and help me understand Tripwire.

Now i have wrote two full HOWTOs on Swedish forum boards.
This might help others and all this because of your help.

Thanks Gyokuro.

Now i have a expensive gaming computer at home as family computer.
I been thinking to change that computer from Windows 8 to Ubuntu 12.04 LTS
And now i feel more secure doing so as i learn how to use Tripwire.

My next project is to learn how to create a complete back up system for Ubuntu.
Then i feel i have everything i need to safe guard my Ubuntu system.

Cheers

---

### Post by Gyokuro on 2014-07-22
Hi

No problem and thank you for your nice Tripwire How-to - I think all your problems are solved and in case everything got solved could you please tag this thread as solved? Have fun and in case of problems come back to the forums :-)

---

### Post by patrikmellq on 2014-07-23
Hello Gyokuro, i fix the topic as solved.
And for all here is the complete howto [http://ubuntuforums.org/showthread.php?t=2235300](http://ubuntuforums.org/showthread.php?t=2235300)

Cheers

---

