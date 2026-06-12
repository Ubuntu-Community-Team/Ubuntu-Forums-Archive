---
title: "Uninstalling Drop Box"
date: 2014-09-04
forum: Ubuntu Studio
---

### Post by themuseman on 2014-09-04
I have been using Ubuntu since 2012 but have not had to maintain or change or administer much on this system. So I'm basically a novice. I'm running 12.04 amd64. 

I was trying to update DropBox. I did search the forums, as best I could. I uninstalled it (as far as I could tell). Then tried to install a current version from the DropBox web site. So far in, it hung up, terminal said it was 100% installed, but that's where it hung.

I thought, OK, I'll just uninstall it

I tried to uninstall it without success. Here's the terminal data:

~$ sudo apt-get remove nautilus-dropbox
[sudo] password for caretaker: 
Sorry, try again.
[sudo] password for caretaker: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
~$ 

Oh, and the old version is somehow still working, I just want to totally uninstall it now. Help would be much appreciated.

---

### Post by themuseman on 2014-09-04
Actually the terminal read 100% downloaded, and then it hung there.

---

### Post by mörgæs on 2014-09-05
What happens if you reboot and run
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove nautilus-dropbox
```
?

---

### Post by themuseman on 2014-09-05
Morgaes,

I have rebooted.
Then I ran:  sudo apt-get upgrade
After a long listing, apparently without any errors, here are the last few lines:

Fetched 4,807 kB in 8s (592 kB/s)                                              
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
caretaker@larry-pc:~$ 

Should I run:  sudo dpkg --configure -a

---

### Post by themuseman on 2014-09-05
Morgaes,

Ooooops ....
I ran: sudo apt-get update, then received the listing above

---

### Post by themuseman on 2014-09-06
So I ran: "sudo apt-get update"

And I got this as the final few lines: 

"Fetched 4,807 kB in 8s (592 kB/s)                                              
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

So I ran: "sudo dpkg --configure -a"

And I got this:

"Setting up nautilus-dropbox (0.7.1-2) ...

Downloading Dropbox... 100%^CTraceback (most recent call last):. Want to learn m  File "/usr/bin/dropbox", line 1384, in <module>
    ret = main(sys.argv)
  File "/usr/bin/dropbox", line 1373, in main
    result = commands[argv[i]](argv[i+1:])
  File "/usr/bin/dropbox", line 806, in update
    download()
  File "/usr/bin/dropbox", line 534, in download
    progress = one_chunk.next()[0]
  File "/usr/bin/dropbox", line 209, in download_file_chunk
    chunk = os.read(f.fileno(), 4096)
KeyboardInterrupt
dpkg: error processing nautilus-dropbox (--configure):
 subprocess installed post-installation script was interrupted
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nautilus-dropbox"

It acually hung after: "Downloading Dropbox... 100%" but in an attempt to copy the teminal display, I highlighted the listing and pressed "^C"  instead of right clicking the mouse. Hence the additional text after "... 100%"

But that's where it hung...again, after dropbox was downloaded. 

This last listing indicates that it is trying to install "nautilus-dropbox (0.7.1-2)", but that is the version that is installed, that I want to update or as a last resort, just eliminate. Is it possible that after I "Quit" DropBox (before I did the above work), that something is still active? Referring to my original post, the listing is asking the question: Is another process using "/var/lib/dpkg"? How can I tell?

---

### Post by mörgæs on 2014-09-07
Ctrl+C in a terminal cancels a comand. If you want to copy to and from it's better to use the mouse.

If we forget Dropbox or a moment, please run

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and post the complete output in CODE tags.

---

### Post by themuseman on 2014-09-08
Ok...Here is the listing of the output of both commands...

```

~$ sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Get:2 http://us.archive.ubuntu.com precise-updates Release [98.7 kB]           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:3 http://us.archive.ubuntu.com precise-updates/main Sources [479 kB]       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:4 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:5 http://us.archive.ubuntu.com precise-updates/universe Sources [110 kB]   
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:7 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [831 kB]
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:8 https://private-ppa.launchpad.net precise/main TranslationIndex [369 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:9 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:10 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [248 kB]
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/main i386 Packages [862 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [254 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:18 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:19 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Get:20 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Get:21 http://security.ubuntu.com precise-security Release [50.7 kB]
Get:22 http://security.ubuntu.com precise-security/main Sources [110 kB]
Get:23 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:24 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]
Get:25 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]
Get:26 http://security.ubuntu.com precise-security/main amd64 Packages [421 kB]
Get:27 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:28 http://security.ubuntu.com precise-security/universe amd64 Packages [97.4 kB]
Get:29 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,451 B]
Get:30 http://security.ubuntu.com precise-security/main i386 Packages [451 kB] 
Get:31 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:32 http://security.ubuntu.com precise-security/universe i386 Packages [103 kB]
Get:33 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Get:34 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:35 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:36 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:37 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 4,253 kB in 6s (609 kB/s)                                              
Reading package lists... Done
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  lib32gcc1 libc6-i386 linux-headers-3.2.0-68
  linux-headers-3.2.0-68-lowlatency linux-image-3.2.0-68-lowlatency nvidia-304
  nvidia-304-updates
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-ppdc firefox firefox-globalmenu
  firefox-locale-en gnupg gpgv libc-bin libc-dev-bin libc6 libc6:i386
  libc6-dev libcups2 libcups2:i386 libcups2-dev libcupscgi1 libcupsdriver1
  libcupsimage2 libcupsimage2-dev libcupsmime1 libcupsppdc1 libgcrypt11
  libgcrypt11:i386 libgcrypt11-dev liblua5.1-0 linux-headers-lowlatency
  linux-image-lowlatency linux-libc-dev linux-lowlatency multiarch-support
  nvidia-current nvidia-current-updates rsyslog
36 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 254 MB of archives.
After this operation, 231 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc-bin amd64 2.15-0ubuntu10.7 [1,181 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc-dev-bin amd64 2.15-0ubuntu10.7 [83.9 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-dev amd64 2.15-0ubuntu10.7 [2,941 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 i386 2.15-0ubuntu10.7 [3,942 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 amd64 2.15-0ubuntu10.7 [4,654 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-libc-dev amd64 3.2.0-68.102 [861 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgcrypt11-dev amd64 1.5.0-3ubuntu0.3 [364 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgcrypt11 i386 1.5.0-3ubuntu0.3 [282 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgcrypt11 amd64 1.5.0-3ubuntu0.3 [281 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsimage2-dev amd64 1.5.3-0ubuntu8.5 [65.5 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsimage2 amd64 1.5.3-0ubuntu8.5 [51.8 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcups2-dev amd64 1.5.3-0ubuntu8.5 [243 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcups2 amd64 1.5.3-0ubuntu8.5 [168 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcups2 i386 1.5.3-0ubuntu8.5 [170 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsmime1 amd64 1.5.3-0ubuntu8.5 [13.5 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcupscgi1 amd64 1.5.3-0ubuntu8.5 [29.8 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsppdc1 amd64 1.5.3-0ubuntu8.5 [52.4 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main cups-common all 1.5.3-0ubuntu8.5 [820 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main cups-bsd amd64 1.5.3-0ubuntu8.5 [44.7 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main cups-client amd64 1.5.3-0ubuntu8.5 [175 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main cups-ppdc amd64 1.5.3-0ubuntu8.5 [30.9 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main cups amd64 1.5.3-0ubuntu8.5 [1,293 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsdriver1 amd64 1.5.3-0ubuntu8.5 [19.6 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main liblua5.1-0 amd64 5.1.4-12ubuntu1.1 [172 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe linux-image-3.2.0-68-lowlatency amd64 3.2.0-68.70 [38.6 MB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gpgv amd64 1.4.11-3ubuntu2.7 [186 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gnupg amd64 1.4.11-3ubuntu2.7 [806 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main multiarch-support amd64 2.15-0ubuntu10.7 [4,484 B]
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main rsyslog amd64 5.8.6-1ubuntu8.7 [428 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox amd64 32.0+build1-0ubuntu0.12.04.1 [42.0 MB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-globalmenu amd64 32.0+build1-0ubuntu0.12.04.1 [8,960 B]
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-en amd64 32.0+build1-0ubuntu0.12.04.1 [753 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.7 [3,992 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-68 all 3.2.0-68.102 [11.7 MB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe linux-headers-3.2.0-68-lowlatency amd64 3.2.0-68.70 [991 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe linux-lowlatency amd64 3.2.0.68.56 [1,724 B]
Get:37 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe linux-image-lowlatency amd64 3.2.0.68.56 [2,304 B]
Get:38 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe linux-headers-lowlatency amd64 3.2.0.68.56 [2,296 B]
Get:39 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32gcc1 amd64 1:4.6.3-1ubuntu5 [54.1 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-304 amd64 304.116-0ubuntu0.0.1 [68.3 MB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-304-updates amd64 304.116-0ubuntu0.0.1 [68.3 MB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-current amd64 304.116-0ubuntu0.0.1 [4,504 B]
Get:43 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-current-updates amd64 304.116-0ubuntu0.0.1 [4,516 B]
Fetched 254 MB in 4min 33s (927 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 290916 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.6 (using .../libc-bin_2.15-0ubuntu10.7_amd64.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for man-db ...
Setting up libc-bin (2.15-0ubuntu10.7) ...
(Reading database ... 290916 files and directories currently installed.)
Preparing to replace libc-dev-bin 2.15-0ubuntu10.6 (using .../libc-dev-bin_2.15-0ubuntu10.7_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.15-0ubuntu10.6 (using .../libc6-dev_2.15-0ubuntu10.7_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6 2.15-0ubuntu10.6 (using .../libc6_2.15-0ubuntu10.7_amd64.deb) ...
De-configuring libc6:i386 ...
Unpacking replacement libc6 ...
Preparing to replace libc6:i386 2.15-0ubuntu10.6 (using .../libc6_2.15-0ubuntu10.7_i386.deb) ...
Unpacking replacement libc6:i386 ...
Processing triggers for man-db ...
Setting up libc6 (2.15-0ubuntu10.7) ...
Setting up libc6:i386 (2.15-0ubuntu10.7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 290916 files and directories currently installed.)
Preparing to replace linux-libc-dev 3.2.0-67.101 (using .../linux-libc-dev_3.2.0-68.102_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace libgcrypt11-dev 1.5.0-3ubuntu0.2 (using .../libgcrypt11-dev_1.5.0-3ubuntu0.3_amd64.deb) ...
Unpacking replacement libgcrypt11-dev ...
Preparing to replace libgcrypt11:i386 1.5.0-3ubuntu0.2 (using .../libgcrypt11_1.5.0-3ubuntu0.3_i386.deb) ...
De-configuring libgcrypt11 ...
Unpacking replacement libgcrypt11:i386 ...
Preparing to replace libgcrypt11 1.5.0-3ubuntu0.2 (using .../libgcrypt11_1.5.0-3ubuntu0.3_amd64.deb) ...
Unpacking replacement libgcrypt11 ...
Processing triggers for man-db ...
Setting up libgcrypt11:i386 (1.5.0-3ubuntu0.3) ...
Setting up libgcrypt11 (1.5.0-3ubuntu0.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 290916 files and directories currently installed.)
Preparing to replace libcupsimage2-dev 1.5.3-0ubuntu8.4 (using .../libcupsimage2-dev_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcupsimage2-dev ...
Preparing to replace libcupsimage2 1.5.3-0ubuntu8.4 (using .../libcupsimage2_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcupsimage2 ...
Preparing to replace libcups2-dev 1.5.3-0ubuntu8.4 (using .../libcups2-dev_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcups2-dev ...
Preparing to replace libcups2:i386 1.5.3-0ubuntu8.4 (using .../libcups2_1.5.3-0ubuntu8.5_i386.deb) ...
De-configuring libcups2 ...
Unpacking replacement libcups2:i386 ...
Preparing to replace libcups2 1.5.3-0ubuntu8.4 (using .../libcups2_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcups2 ...
Processing triggers for man-db ...
Setting up libcups2:i386 (1.5.3-0ubuntu8.5) ...
Setting up libcups2 (1.5.3-0ubuntu8.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 290916 files and directories currently installed.)
Preparing to replace libcupsmime1 1.5.3-0ubuntu8.4 (using .../libcupsmime1_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcupsmime1 ...
Preparing to replace libcupscgi1 1.5.3-0ubuntu8.4 (using .../libcupscgi1_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcupscgi1 ...
Preparing to replace libcupsppdc1 1.5.3-0ubuntu8.4 (using .../libcupsppdc1_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcupsppdc1 ...
Preparing to replace cups-common 1.5.3-0ubuntu8.4 (using .../cups-common_1.5.3-0ubuntu8.5_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.5.3-0ubuntu8.4 (using .../cups-bsd_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.5.3-0ubuntu8.4 (using .../cups-client_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement cups-client ...
Preparing to replace cups-ppdc 1.5.3-0ubuntu8.4 (using .../cups-ppdc_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement cups-ppdc ...
Preparing to replace cups 1.5.3-0ubuntu8.4 (using .../cups_1.5.3-0ubuntu8.5_amd64.deb) ...
cups stop/waiting
Unpacking replacement cups ...
Preparing to replace libcupsdriver1 1.5.3-0ubuntu8.4 (using .../libcupsdriver1_1.5.3-0ubuntu8.5_amd64.deb) ...
Unpacking replacement libcupsdriver1 ...
Preparing to replace liblua5.1-0 5.1.4-12ubuntu1 (using .../liblua5.1-0_5.1.4-12ubuntu1.1_amd64.deb) ...
Unpacking replacement liblua5.1-0 ...
Selecting previously unselected package linux-image-3.2.0-68-lowlatency.
Unpacking linux-image-3.2.0-68-lowlatency (from .../linux-image-3.2.0-68-lowlatency_3.2.0-68.70_amd64.deb) ...
Done.
Preparing to replace gpgv 1.4.11-3ubuntu2.6 (using .../gpgv_1.4.11-3ubuntu2.7_amd64.deb) ...
Unpacking replacement gpgv ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Setting up gpgv (1.4.11-3ubuntu2.7) ...
(Reading database ... 295054 files and directories currently installed.)
Preparing to replace gnupg 1.4.11-3ubuntu2.6 (using .../gnupg_1.4.11-3ubuntu2.7_amd64.deb) ...
Unpacking replacement gnupg ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up gnupg (1.4.11-3ubuntu2.7) ...
(Reading database ... 295054 files and directories currently installed.)
Preparing to replace multiarch-support 2.15-0ubuntu10.6 (using .../multiarch-support_2.15-0ubuntu10.7_amd64.deb) ...
Unpacking replacement multiarch-support ...
Setting up multiarch-support (2.15-0ubuntu10.7) ...
(Reading database ... 295054 files and directories currently installed.)
Preparing to replace rsyslog 5.8.6-1ubuntu8.6 (using .../rsyslog_5.8.6-1ubuntu8.7_amd64.deb) ...
Unpacking replacement rsyslog ...
Preparing to replace firefox 31.0+build1-0ubuntu0.12.04.1 (using .../firefox_32.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 31.0+build1-0ubuntu0.12.04.1 (using .../firefox-globalmenu_32.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 31.0+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_32.0+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Selecting previously unselected package libc6-i386.
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10.7_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Selecting previously unselected package linux-headers-3.2.0-68.
Unpacking linux-headers-3.2.0-68 (from .../linux-headers-3.2.0-68_3.2.0-68.102_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-68-lowlatency.
Unpacking linux-headers-3.2.0-68-lowlatency (from .../linux-headers-3.2.0-68-lowlatency_3.2.0-68.70_amd64.deb) ...
Preparing to replace linux-lowlatency 3.2.0.48.37 (using .../linux-lowlatency_3.2.0.68.56_amd64.deb) ...
Unpacking replacement linux-lowlatency ...
Preparing to replace linux-image-lowlatency 3.2.0.48.37 (using .../linux-image-lowlatency_3.2.0.68.56_amd64.deb) ...
Unpacking replacement linux-image-lowlatency ...
Preparing to replace linux-headers-lowlatency 3.2.0.48.37 (using .../linux-headers-lowlatency_3.2.0.68.56_amd64.deb) ...
Unpacking replacement linux-headers-lowlatency ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package nvidia-304.
Unpacking nvidia-304 (from .../nvidia-304_304.116-0ubuntu0.0.1_amd64.deb) ...
Selecting previously unselected package nvidia-304-updates.
Unpacking nvidia-304-updates (from .../nvidia-304-updates_304.116-0ubuntu0.0.1_amd64.deb) ...
Preparing to replace nvidia-current 304.88-0ubuntu0.0.2 (using .../nvidia-current_304.116-0ubuntu0.0.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
dpkg: warning: unable to delete old directory '/usr/lib32/nvidia-current': Directory not empty
dpkg: warning: unable to delete old directory '/usr/lib/nvidia-current': Directory not empty
Preparing to replace nvidia-current-updates 304.88-0ubuntu0.0.1 (using .../nvidia-current-updates_304.116-0ubuntu0.0.1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current-updates ...
dpkg: warning: unable to delete old directory '/usr/lib/nvidia-current-updates': Directory not empty
dpkg: warning: unable to delete old directory '/usr/lib32/nvidia-current-updates': Directory not empty
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Setting up libc-dev-bin (2.15-0ubuntu10.7) ...
Setting up linux-libc-dev (3.2.0-68.102) ...
Setting up libc6-dev (2.15-0ubuntu10.7) ...
Setting up nautilus-dropbox (0.7.1-2) ...

Dropbox is the easiest way to share and store your files online. Want to learn more? Head to http://www.dropbox.com/

Downloading Dropbox... 100%

```

This is where ist stops... it hangs here... stuck...

---

### Post by mörgæs on 2014-09-09
Please carry on trying commands on your own, you don't have to wait for me.

What about a reboot and 
```
sudo apt-get remove nautilus-dropbox
```
or
```
sudo apt-get --purge remove nautilus-dropbox
```
?

---

### Post by themuseman on 2014-09-09
Any suggestions for a central resource of commonly used Ubuntu terminal commands?

---

### Post by themuseman on 2014-09-09
[FONT=arial]I think I have it uninstalled now. Here is a summary of this entire situation:

[/FONT][FONT=arial]   [/FONT][FONT=arial][SIZE=2]DropBox ver 0.7.xx was already installed. Running install again really goofed things up. I thought I was installing the latest version, but apparently
 I wasn't. Since I goofed it up, I wanted to uninstall it. [/SIZE][SIZE=2]I tried various commands to uninstall it, without success. Finally, I did the following:[/SIZE]
[/FONT][FONT=arial][/FONT][FONT=arial]```
sudo 	dpkg --configure -a 	 	[/FONT]
```

[FONT=arial][/FONT][FONT=arial][SIZE=2]During this process, it downloaded DropBox again. When it reached Download=100%, the program hung up. I pressed 	[/SIZE][SIZE=2]Ctrl[/SIZE][SIZE=2]+[/SIZE][SIZE=2]C[/SIZE][SIZE=2] and more code was executed. When it finished I did:
[/SIZE][/FONT]
[FONT=arial][/FONT][FONT=arial]```
sudo 	apt-get purge nautilus-dropbox[SIZE=2] [/SIZE][/FONT][SIZE=2]
```[/SIZE]

[FONT=arial][/FONT][FONT=arial][SIZE=2]It seemed to be uninstalled. For more clean up, I ran:[/SIZE][/FONT]

```


[FONT=arial][/FONT][FONT=arial][SIZE=2]rm 	-rf ~/.dropbox[/SIZE][/FONT]
[FONT=arial][/FONT][FONT=arial][SIZE=2]rm 	-rf ~/.dropbox-dist[/SIZE]

```[/FONT]
[FONT=arial] [/FONT][FONT=arial]
[/FONT]
[FONT=arial][/FONT][FONT=arial]  [SIZE=2]DropBox now seems to have been uninstalled.[/SIZE][/FONT][FONT=arial][/FONT]

Now it seems I'm back to the very beginning, and that's "How do I get the latest version of DropBox, the preferred way?" Can someone help me with this?

---

### Post by themuseman on 2014-09-09
Here's what I finally did:

```

sudo dpkg --configure -a

```

When DropBox Download=100%, the program hung. Then I did a 'Control C'. After a little more code ran, and said Done, I did this:

```

sudo apt-get purge nautilus-dropbox

```

That seemed to have uninstalled it. As suggested in another post I ran this:
```

rm -rf ~/.dropbox
rm -rf ~/.dropbox-dist

```

Now that its uninstalled, how do I install the latest version of DropBox(best way possible)?

---

### Post by mörgæs on 2014-09-09
Congratulations. I don't use Dropbox and have no experience installing it, sorry.

---

### Post by vasa1 on 2014-09-09
Do you see any sort of errors or warnings while/after running **sudo apt-get update** and then **sudo apt-get upgrade**?

If you're satisfied that your system is now working properly, take a look at [http://ubuntuforums.org/showthread.php?t=2240094&p=13114855#post13114855](http://ubuntuforums.org/showthread.php?t=2240094&p=13114855#post13114855)

BTW, why do you have **backports** and **private-ppa** as part of your sources?

---

### Post by themuseman on 2014-09-10
> **vasa1 said:**
> Do you see any sort of errors or warnings while/after running **sudo apt-get update** and then **sudo apt-get upgrade**?

If you're satisfied that your system is now working properly, take a look at [http://ubuntuforums.org/showthread.php?t=2240094&p=13114855#post13114855](http://ubuntuforums.org/showthread.php?t=2240094&p=13114855#post13114855)

BTW, why do you have **backports** and **private-ppa** as part of your sources?

1. I ran **sudo apt-get update** and then **sudo apt-get upgrade** again ... no errors or warnings.

2. I looked over the thread you referred to ... if I install dropbox manually as you did, when it becomes necessay, how do I update it? 
Also, I was going to use dropbox to distribute files to a group I am working with (most of them have Windows). Is there a better cloud file sharing server I should consider?

3. The Launchpad ppa was to update OpenShot Video Editor over a year ago. I needed the latest version (back when I did this). Was there a better way to update it? ....I don't know anything about the backports....did that come along with the PPAs?
Also, the Software Center set up a Launchpad ppa for Master PDF Editor, which I do not use...now using Adobe Reader 9. 

Any suggestions concerning what I have done, what I ought to have done, or what I should do in the future is greatly appreciated as I am still trying to get on firm ground in the Ubuntu world.

---

### Post by CrocoDuck on 2014-09-11
> **themuseman said:**
>  Is there a better cloud file sharing server I should consider?

Hi! Dropbox is a nice program, I use it everyday. Anyway, [this service]("https://www.wetransfer.com/") is very easy to use and powerful, it does not even require to install software, it is completely OS independent. Give it a go if you want.

Also, I suggest you to have a look at [this]("https://www.teamviewer.com/en/index.aspx"). Its main purpose is not file sharing, but you can share files with that. If you need software for work, meetings and so, that one is gonna be useful.

---

