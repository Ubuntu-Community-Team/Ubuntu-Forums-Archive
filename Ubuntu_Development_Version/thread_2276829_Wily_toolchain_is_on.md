---
title: "Wily toolchain is on"
date: 2015-05-05
forum: Ubuntu Development Version
---

### Post by slickymaster on 2015-05-05
Nothing much at the moment, but the toolchain is already on:```
~$ sudo apt-get update && sudo apt-get dist-upgrade 
[sudo] password for slickymaster: 
Ign http://dl.google.com stable InRelease
Ign http://security.ubuntu.com wily-security InRelease                         
Ign http://extras.ubuntu.com wily InRelease                                    
Ign http://pt.archive.ubuntu.com wily InRelease                                
Ign http://archive.canonical.com wily InRelease                      
Hit http://dl.google.com stable Release.gpg                          
Ign http://pt.archive.ubuntu.com wily-updates InRelease                        
Ign http://extras.ubuntu.com wily Release.gpg                                  
Hit http://security.ubuntu.com wily-security Release.gpg                       
Hit http://archive.canonical.com wily Release.gpg                    
Ign http://pt.archive.ubuntu.com wily-backports InRelease                      
Hit http://dl.google.com stable Release                                        
Ign http://pt.archive.ubuntu.com wily-proposed InRelease                       
Hit http://security.ubuntu.com wily-security Release                           
Hit http://archive.canonical.com wily Release                                  
Ign http://extras.ubuntu.com wily Release                                      
Hit http://pt.archive.ubuntu.com wily Release.gpg                              
Hit http://pt.archive.ubuntu.com wily-updates Release.gpg            
Hit http://pt.archive.ubuntu.com wily-backports Release.gpg          
Hit http://pt.archive.ubuntu.com wily-proposed Release.gpg            
Hit http://pt.archive.ubuntu.com wily Release                                  
Get:1 http://dl.google.com stable/main i386 Packages [1197 B]                  
Hit http://pt.archive.ubuntu.com wily-updates Release                          
Hit http://pt.archive.ubuntu.com wily-backports Release               
Hit http://pt.archive.ubuntu.com wily-proposed Release                
Hit http://archive.canonical.com wily/partner Sources                                                            
Hit http://archive.canonical.com wily/partner i386 Packages                                                      
Hit http://archive.canonical.com wily/partner Translation-en                                                                    
Ign http://dl.google.com stable/main Translation-en_US                                                           
Ign http://dl.google.com stable/main Translation-en                                        
Get:2 http://security.ubuntu.com wily-security/main Sources [28 B]                         
Hit http://pt.archive.ubuntu.com wily/main Sources                     
Get:3 http://security.ubuntu.com wily-security/restricted Sources [28 B]
Get:4 http://security.ubuntu.com wily-security/universe Sources [28 B]               
Err http://extras.ubuntu.com wily/main Sources                                           
  404  Not Found
Get:5 http://security.ubuntu.com wily-security/multiverse Sources [28 B]
Err http://extras.ubuntu.com wily/main i386 Packages             
  404  Not Found
Ign http://extras.ubuntu.com wily/main Translation-en_US                               
Get:6 http://security.ubuntu.com wily-security/main i386 Packages [28 B]               
Ign http://extras.ubuntu.com wily/main Translation-en                                     
Get:7 http://security.ubuntu.com wily-security/restricted i386 Packages [28 B]         
Get:8 http://security.ubuntu.com wily-security/universe i386 Packages [28 B]
Get:9 http://security.ubuntu.com wily-security/multiverse i386 Packages [28 B]
Hit http://security.ubuntu.com wily-security/main Translation-en
Hit http://security.ubuntu.com wily-security/multiverse Translation-en
Hit http://security.ubuntu.com wily-security/restricted Translation-en
Hit http://security.ubuntu.com wily-security/universe Translation-en
Hit http://pt.archive.ubuntu.com wily/restricted Sources
Hit http://pt.archive.ubuntu.com wily/universe Sources
Hit http://pt.archive.ubuntu.com wily/multiverse Sources
Hit http://pt.archive.ubuntu.com wily/main i386 Packages
Hit http://pt.archive.ubuntu.com wily/restricted i386 Packages
Hit http://pt.archive.ubuntu.com wily/universe i386 Packages
Hit http://pt.archive.ubuntu.com wily/multiverse i386 Packages
Hit http://pt.archive.ubuntu.com wily/main Translation-en
Hit http://pt.archive.ubuntu.com wily/multiverse Translation-en
Hit http://pt.archive.ubuntu.com wily/restricted Translation-en
Hit http://pt.archive.ubuntu.com wily/universe Translation-en
Hit http://pt.archive.ubuntu.com wily-updates/main Sources
Hit http://pt.archive.ubuntu.com wily-updates/restricted Sources
Hit http://pt.archive.ubuntu.com wily-updates/universe Sources
Hit http://pt.archive.ubuntu.com wily-updates/multiverse Sources
Hit http://pt.archive.ubuntu.com wily-updates/main i386 Packages                                                                                            
Hit http://pt.archive.ubuntu.com wily-updates/restricted i386 Packages                                                                                      
Hit http://pt.archive.ubuntu.com wily-updates/universe i386 Packages                                                                                        
Hit http://pt.archive.ubuntu.com wily-updates/multiverse i386 Packages                                                                                      
Hit http://pt.archive.ubuntu.com wily-updates/main Translation-en                                                                                           
Hit http://pt.archive.ubuntu.com wily-updates/multiverse Translation-en                                                                                     
Hit http://pt.archive.ubuntu.com wily-updates/restricted Translation-en                                                                                     
Hit http://pt.archive.ubuntu.com wily-updates/universe Translation-en                                                                                       
Hit http://pt.archive.ubuntu.com wily-backports/main Sources                                                                                                
Hit http://pt.archive.ubuntu.com wily-backports/restricted Sources                                                                                          
Hit http://pt.archive.ubuntu.com wily-backports/universe Sources                                                                                            
Hit http://pt.archive.ubuntu.com wily-backports/multiverse Sources                                                                                          
Hit http://pt.archive.ubuntu.com wily-backports/main i386 Packages                                                                                          
Hit http://pt.archive.ubuntu.com wily-backports/restricted i386 Packages                                                                                    
Hit http://pt.archive.ubuntu.com wily-backports/universe i386 Packages                                                                                      
Hit http://pt.archive.ubuntu.com wily-backports/multiverse i386 Packages                                                                                    
Hit http://pt.archive.ubuntu.com wily-backports/main Translation-en                                                                                         
Hit http://pt.archive.ubuntu.com wily-backports/multiverse Translation-en                                                                                   
Hit http://pt.archive.ubuntu.com wily-backports/restricted Translation-en                                                                                   
Hit http://pt.archive.ubuntu.com wily-backports/universe Translation-en                                                                                     
Hit http://pt.archive.ubuntu.com wily-proposed/main i386 Packages                                                                                           
Hit http://pt.archive.ubuntu.com wily-proposed/restricted i386 Packages                                                                                     
Hit http://pt.archive.ubuntu.com wily-proposed/universe i386 Packages                                                                                       
Hit http://pt.archive.ubuntu.com wily-proposed/multiverse i386 Packages                                                                                     
Hit http://pt.archive.ubuntu.com wily-proposed/main Translation-en                                                                                          
Hit http://pt.archive.ubuntu.com wily-proposed/multiverse Translation-en                                                                                    
Hit http://pt.archive.ubuntu.com wily-proposed/restricted Translation-en                                                                                    
Hit http://pt.archive.ubuntu.com wily-proposed/universe Translation-en                                                                                      
Fetched 224 B in 13s (16 B/s)                                                                                                                               
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/wily/main/source/Sources  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily
3.19.0-16-generic
```

---

### Post by ventrical on 2015-05-05
Yep..

```

ventrical@ventrical-luntiy-betatest:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by raonyguimaraes on 2015-05-05
What is the easiest way to upgrade from 15.04 ?

---

### Post by cariboo on 2015-05-05
> **raonyguimaraes said:**
> What is the easiest way to upgrade from 15.04 ?

```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
```

Run the above command in a terminal, then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Note:** I'll be updating [this]("http://ubuntuforums.org/showthread.php?t=2249680") thread a little later today.

---

### Post by ventrical on 2015-05-05
> **raonyguimaraes said:**
> What is the easiest way to upgrade from 15.04 ?

Read this here:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

Regards..

---

### Post by ventrical on 2015-05-05
> **cariboo said:**
> ```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
```

Run the above command in a terminal.

Ahh .. beat me to it ! :)

---

### Post by slickymaster on 2015-05-05
> **raonyguimaraes said:**
> What is the easiest way to upgrade from 15.04 ?
Here you go: [How can I upgrade to the next version]("https://wiki.ubuntu.com/U%2B1/common-problems#How_can_I_upgrade_to_the_next_version")
Please take in considerattion that the wiki ^^^ isn't yet updated to showcase the update to wily. It's still referring to update from Utopic to Vivid, so you'll have to make the necessary adjustments, like:```
sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list
```instead of```
sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list
```
Also, all occurrences of vivid will have to be replaced by wily in the block to be inserted in ```
/usr/share/python-apt/templates/Ubuntu.info
```if you come to face [this issue with your Software & Updates]("https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work")

---

### Post by slickymaster on 2015-05-05
:lolflag:
beaten by the two of you :p

---

### Post by ventrical on 2015-05-05
> **slickymaster said:**
> :lolflag:
beaten by the two of you :p

Thanks for pointing out wiki code. I have to change the sudo command at testers wiki.

Regards..

---

### Post by cariboo on 2015-05-05
Didn't some one come up with a one line solution to fixing /usr/share/python-apt/templates/Ubuntu.info? I know if you use synaptic exclusively the problem gets fixed automagically.

---

### Post by ventrical on 2015-05-05
> **cariboo said:**
> Didn't some one come up with a one line solution to fixing /usr/share/python-apt/templates/Ubuntu.info? I know if you use synaptic exclusively the problem gets fixed automagically.

Yes.

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

But you haven't edited /vivid/ to /wily/ yet.

Regards..

---

### Post by ventrical on 2015-05-05
> **cariboo said:**
> 

**Note:** I'll be updating [this]("http://ubuntuforums.org/showthread.php?t=2249680") thread a little later today.

Ahhh ..  beat me again. :)

Regards..

---

### Post by raonyguimaraes on 2015-05-05
Thank you guys!
```

$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily

$ uname -a
Linux darwin 4.1.0-040100rc2-generic #201505032335 SMP Mon May 4 03:36:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by slickymaster on 2015-05-05
> **cariboo said:**
> Didn't some one come up with a one line solution to fixing /usr/share/python-apt/templates/Ubuntu.info? I know if you use synaptic exclusively the problem gets fixed automagically.
> **ventrical said:**
> Yes.

[https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

But you haven't edited /vivid/ to /wily/ yet.

Regards..
Not sure cariboo was referring to that. That's hardly a one line solution.

---

### Post by ventrical on 2015-05-05
> **slickymaster said:**
> Not sure cariboo was referring to that. That's hardly a one line solution.

We just copy and past the ubuntu.info file but not the one at the outdated link.

---

### Post by ventrical on 2015-05-05
ubuntu.info defaults to:

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


```

atm.

---

### Post by slickymaster on 2015-05-05
> **ventrical said:**
> We just copy and past the ubuntu.info file but not the one at the outdated link.
Yes. But as cariboo mentioned a one liner solution I got the impression that we'd be talking about something else.

---

### Post by QDR06VV9 on 2015-05-05
> **cariboo said:**
> Didn't some one come up with a one line solution to fixing /usr/share/python-apt/templates/Ubuntu.info? I know if you use synaptic exclusively the problem gets fixed automagically.
Is this the one your looking for #post 31??
[http://ubuntuforums.org/showthread.php?t=2181414&page=4](http://ubuntuforums.org/showthread.php?t=2181414&page=4)
Whoops should have read all the pages first! My Bad!!
```
sudo sed -i 's/vivid/devel/g' /etc/apt/sources.list
```
From here Post #53 [http://ubuntuforums.org/showthread.php?t=2181414&page=6](http://ubuntuforums.org/showthread.php?t=2181414&page=6)
Ventrical and Zika have saved my bucket more than once!
Thanks Guys:popcorn:

---

### Post by ventrical on 2015-05-05
> **runrickus said:**
> Is this the one your looking for #post 31??
[http://ubuntuforums.org/showthread.php?t=2181414&page=4](http://ubuntuforums.org/showthread.php?t=2181414&page=4)
Whoops should have read all the pages first! My Bad!!
```
sudo sed -i 's/vivid/devel/g' /etc/apt/sources.list
```
From here Post #53 [http://ubuntuforums.org/showthread.php?t=2181414&page=6](http://ubuntuforums.org/showthread.php?t=2181414&page=6)
Ventrical and Zika have saved my bucket more than once!
Thanks Guys:popcorn:

The ubuntu.info file usually comes down the pipe a little later.;)  but not much later.

Regards..

---

### Post by cariboo on 2015-05-05
I know I saw a one line command that changed the current release to the testing version of /usr/share/python-apt/templates/Ubuntu.info, because using gedit to  search and replace the version names is a bit more than a one line solution.

---

### Post by ventrical on 2015-05-05
> **cariboo said:**
> I know I saw a one line command that changed the current release to the testing version of /usr/share/python-apt/templates/Ubuntu.info, because using gedit to  search and replace the version names is a bit more than a one line solution.

[http://ubuntuforums.org/showthread.php?t=2181414&page=7&p=12827219#post12827219](http://ubuntuforums.org/showthread.php?t=2181414&page=7&p=12827219#post12827219)

Regards..

---

### Post by ventrical on 2015-05-05
> **ventrical said:**
> [http://ubuntuforums.org/showthread.php?t=2181414&page=7&p=12827219#post12827219](http://ubuntuforums.org/showthread.php?t=2181414&page=7&p=12827219#post12827219)

Regards..

Yikes!!  Don't do it ! :)

I half foobarred my system. hehehe .. finally some fun :)

Regards..

---

### Post by ventrical on 2015-05-05
Ok.. it's working again. I just hand edited the Ubuntu.info file.

```

ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: wily
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: wily-security
ParentSuite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: wily-security
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb
Description: Recommended updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb
Description: Pre-released updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb
Description: Unsupported updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


```

The above method may not be the recommended method nor may it be considered the prudent or contrite method .. but it got Software&Updates working again after it had locked up and gave me a GTK error.

Regards..

---

### Post by QDR06VV9 on 2015-05-05
> **ventrical said:**
> Yikes!!  Don't do it ! :)

I half foobarred my system. hehehe .. finally some fun :)

Regards..
Like a moth to Flame I had to do it.
I hate it when your the only one having the fun;)

---

### Post by ventrical on 2015-05-05
> **runrickus said:**
> Like a moth to Flame I had to do it.
I hate it when your the only one having the fun;)

hehehe .. but the above fixed it :)

Regards..

---

### Post by QDR06VV9 on 2015-05-05
> **ventrical said:**
> hehehe .. but the above fixed it :)

Regards..
You beat me but yes it dose:D

---

### Post by QDR06VV9 on 2015-05-05
So far It has survived 2 hard restarts with kernel 4.0 and nvidia-driver 
DE Mate 64bit
I did however had to recompile pulseaudio from git to get sound to work???](*,)
```
uname -a && sudo lshw -c video && lsb_release -a
Linux me-Aspire-M3300 4.0.0-040000-lowlatency #201504121935 SMP PREEMPT Sun Apr 12 23:45:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[sudo] password for me: 
  *-display               
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:29 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:fa000000-fbffffff ioport:b800(size=128) memory:fe880000-fe8fffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily

```
And upstart so far has been a treat.
```
me@me-Aspire-M3300:~$ !448
pidof systemd && echo "systemd" || echo "other"
other
me@me-Aspire-M3300:~$ !449
pidof /sbin/init && echo "sysvinit" || echo "other"
1
sysvinit

```

---

### Post by sammiev on 2015-05-05
Time to add Wily to the VM and play.

---

### Post by grahammechanical on 2015-05-05
On my vivid to wily repo install I just used Software Updater to bring in the 3.19.0-16 kernel without any issues with Software Updater. And the ubuntu.info file has not been replaced with a file having the references to wily in it.

---

### Post by sammiev on 2015-05-05
lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Wily Werewolf (development branch)
Release:	15.10
Codename:	wily
3.19.0-16-generic

Ready for breakage.

---

### Post by ventrical on 2015-05-06
Welcome aboard! :)

Regards..

---

### Post by slickymaster on 2015-05-06
First updates started to came in, :```
~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files gcc-5-base libatomic1 libcilkrts5 libcurl3 libcurl3-gnutls libgcc1 libgfortran3 libgomp1 libitm1 libquadmath0 libstdc++6 libubsan0 oneconf
  oneconf-common python-apt python-apt-common python-oneconf python3-apt python3-oneconf tzdata
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2189 kB of archives.
After this operation, 846 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://pt.archive.ubuntu.com/ubuntu/ wily/main base-files i386 7.2ubuntu10 [63,3 kB]
Get:2 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main gcc-5-base i386 5.1.1-5ubuntu1 [16,3 kB]
Get:3 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libgcc1 i386 1:5.1.1-5ubuntu1 [46,7 kB]
Get:4 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libstdc++6 i386 5.1.1-5ubuntu1 [424 kB]
Get:5 http://pt.archive.ubuntu.com/ubuntu/ wily/main libcurl3-gnutls i386 7.38.0-3ubuntu3 [189 kB]                                                          
Get:6 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libatomic1 i386 5.1.1-5ubuntu1 [9998 B]                                                       
Get:7 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libcilkrts5 i386 5.1.1-5ubuntu1 [45,2 kB]                                                     
Get:8 http://pt.archive.ubuntu.com/ubuntu/ wily/main libcurl3 i386 7.38.0-3ubuntu3 [198 kB]                                                                 
Get:9 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libquadmath0 i386 5.1.1-5ubuntu1 [204 kB]                                                     
Get:10 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libgfortran3 i386 5.1.1-5ubuntu1 [251 kB]                                                    
Get:11 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libgomp1 i386 5.1.1-5ubuntu1 [59,1 kB]                                                       
Get:12 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libitm1 i386 5.1.1-5ubuntu1 [31,0 kB]                                                        
Get:13 http://pt.archive.ubuntu.com/ubuntu/ wily-proposed/main libubsan0 i386 5.1.1-5ubuntu1 [112 kB]                                                       
Get:14 http://pt.archive.ubuntu.com/ubuntu/ wily/main tzdata all 2015d-1 [183 kB]                                                                           
Get:15 http://pt.archive.ubuntu.com/ubuntu/ wily/main python-apt-common all 0.9.3.11ubuntu1 [16,8 kB]                                                       
Get:16 http://pt.archive.ubuntu.com/ubuntu/ wily/main python3-apt i386 0.9.3.11ubuntu1 [143 kB]                                                             
Get:17 http://pt.archive.ubuntu.com/ubuntu/ wily/main python-apt i386 0.9.3.11ubuntu1 [145 kB]                                                              
Get:18 http://pt.archive.ubuntu.com/ubuntu/ wily/main oneconf-common all 0.3.8 [6086 B]                                                                     
Get:19 http://pt.archive.ubuntu.com/ubuntu/ wily/main python3-oneconf all 0.3.8 [19,6 kB]                                                                   
Get:20 http://pt.archive.ubuntu.com/ubuntu/ wily/main oneconf all 0.3.8 [5530 B]                                                                            
Get:21 http://pt.archive.ubuntu.com/ubuntu/ wily/main python-oneconf all 0.3.8 [19,7 kB]                                                                    
Fetched 2189 kB in 23s (94,2 kB/s)                                                                                                                          
Preconfiguring packages ...
(Reading database ... 190108 files and directories currently installed.)
Preparing to unpack .../base-files_7.2ubuntu10_i386.deb ...
Unpacking base-files (7.2ubuntu10) over (7.2ubuntu9) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for install-info (5.2.0.dfsg.1-6) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic
Setting up base-files (7.2ubuntu10) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...

Configuration file '/etc/lsb-release'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** lsb-release (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/lsb-release ...
Installing new version of config file /etc/os-release ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.0-0ubuntu9) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic
(Reading database ... 190108 files and directories currently installed.)
Preparing to unpack .../gcc-5-base_5.1.1-5ubuntu1_i386.deb ...
Unpacking gcc-5-base:i386 (5.1.1-5ubuntu1) over (5.1~rc1-0ubuntu1) ...
Setting up gcc-5-base:i386 (5.1.1-5ubuntu1) ...
(Reading database ... 190108 files and directories currently installed.)
Preparing to unpack .../libgcc1_1%3a5.1.1-5ubuntu1_i386.deb ...
Unpacking libgcc1:i386 (1:5.1.1-5ubuntu1) over (1:5.1~rc1-0ubuntu1) ...
Setting up libgcc1:i386 (1:5.1.1-5ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 190108 files and directories currently installed.)
Preparing to unpack .../libstdc++6_5.1.1-5ubuntu1_i386.deb ...
Unpacking libstdc++6:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Setting up libstdc++6:i386 (5.1.1-5ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 190109 files and directories currently installed.)
Preparing to unpack .../libcurl3-gnutls_7.38.0-3ubuntu3_i386.deb ...
Unpacking libcurl3-gnutls:i386 (7.38.0-3ubuntu3) over (7.38.0-3ubuntu2.2) ...
Preparing to unpack .../libatomic1_5.1.1-5ubuntu1_i386.deb ...
Unpacking libatomic1:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../libcilkrts5_5.1.1-5ubuntu1_i386.deb ...
Unpacking libcilkrts5:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../libcurl3_7.38.0-3ubuntu3_i386.deb ...
Unpacking libcurl3:i386 (7.38.0-3ubuntu3) over (7.38.0-3ubuntu2.2) ...
Preparing to unpack .../libquadmath0_5.1.1-5ubuntu1_i386.deb ...
Unpacking libquadmath0:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../libgfortran3_5.1.1-5ubuntu1_i386.deb ...
Unpacking libgfortran3:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../libgomp1_5.1.1-5ubuntu1_i386.deb ...
Unpacking libgomp1:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../libitm1_5.1.1-5ubuntu1_i386.deb ...
Unpacking libitm1:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../libubsan0_5.1.1-5ubuntu1_i386.deb ...
Unpacking libubsan0:i386 (5.1.1-5ubuntu1) over (4.9.2-10ubuntu13) ...
Preparing to unpack .../tzdata_2015d-1_all.deb ...
Unpacking tzdata (2015d-1) over (2015d-0ubuntu0.15.04) ...
Setting up tzdata (2015d-1) ...

Current default time zone: 'Europe/Lisbon'
Local time is now:      Qua Mai  6 10:32:53 WEST 2015.
Universal Time is now:  Wed May  6 09:32:53 UTC 2015.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 190111 files and directories currently installed.)
Preparing to unpack .../python-apt-common_0.9.3.11ubuntu1_all.deb ...
Unpacking python-apt-common (0.9.3.11ubuntu1) over (0.9.3.11build1) ...
Preparing to unpack .../python3-apt_0.9.3.11ubuntu1_i386.deb ...
Unpacking python3-apt (0.9.3.11ubuntu1) over (0.9.3.11build1) ...
Preparing to unpack .../python-apt_0.9.3.11ubuntu1_i386.deb ...
Unpacking python-apt (0.9.3.11ubuntu1) over (0.9.3.11build1) ...
Preparing to unpack .../oneconf-common_0.3.8_all.deb ...
Unpacking oneconf-common (0.3.8) over (0.3.7) ...
Preparing to unpack .../python3-oneconf_0.3.8_all.deb ...
Unpacking python3-oneconf (0.3.8) over (0.3.7) ...
Preparing to unpack .../archives/oneconf_0.3.8_all.deb ...
Unpacking oneconf (0.3.8) over (0.3.7) ...
Preparing to unpack .../python-oneconf_0.3.8_all.deb ...
Unpacking python-oneconf (0.3.8) over (0.3.7) ...
Setting up libcurl3-gnutls:i386 (7.38.0-3ubuntu3) ...
Setting up libatomic1:i386 (5.1.1-5ubuntu1) ...
Setting up libcilkrts5:i386 (5.1.1-5ubuntu1) ...
Setting up libcurl3:i386 (7.38.0-3ubuntu3) ...
Setting up libquadmath0:i386 (5.1.1-5ubuntu1) ...
Setting up libgfortran3:i386 (5.1.1-5ubuntu1) ...
Setting up libgomp1:i386 (5.1.1-5ubuntu1) ...
Setting up libitm1:i386 (5.1.1-5ubuntu1) ...
Setting up libubsan0:i386 (5.1.1-5ubuntu1) ...
Setting up python-apt-common (0.9.3.11ubuntu1) ...
Setting up python3-apt (0.9.3.11ubuntu1) ...
Setting up python-apt (0.9.3.11ubuntu1) ...
Setting up oneconf-common (0.3.8) ...
Setting up python3-oneconf (0.3.8) ...
Setting up oneconf (0.3.8) ...
Setting up python-oneconf (0.3.8) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...

```

---

### Post by QDR06VV9 on 2015-05-06
The Wolf Lives.
I have to remember to feed the good wolf..;)
```
inxi -b
System:    Host: me-Aspire-M3300 Kernel: 4.0.0-040000-lowlatency x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 15.10 wily
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 2500.5GB (2.8% used)
Info:      Processes: 202 Uptime: 1:11 Memory: 725.9/5967.1MB
           Client: Shell (bash) inxi: 2.2.16 

```

---

### Post by ventrical on 2015-05-06
Same:

```

ventrical@ventrical-luntiy-betatest:~$ uname -a && sudo lshw -c video && lsb_release -a
Linux ventrical-luntiy-betatest 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[sudo] password for ventrical: 
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:9c00(size=128) memory:fe780000-fe7fffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily
ventrical@ventrical-luntiy-betatest:~$ 

```

but I got a 'broken pipe' error when trying to use upstart from Grub but it is running upstart a lot quicker.

Also .. I have three of these babies--WolfDale processors. Now thats my kind of core :) lol

[http://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB](http://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB)

---

### Post by ventrical on 2015-05-06
.. and ..

```

ventrical@ventrical-luntiy-betatest:~$ inxi -b
System:    Host: ventrical-luntiy-betatest Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed/max: 1998/2997 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1440x900@59.9hz
           GLX Renderer: GeForce 210/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 304.125
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 80.0GB (9.4% used)
Info:      Processes: 178 Uptime: 13 min Memory: 683.8/2000.4MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by QDR06VV9 on 2015-05-06
> **ventrical said:**
> Same:

but I got a 'broken pipe' error when trying to use upstart from Grub but it is running upstart a lot quicker.

Also .. I have three of these babies--WolfDale processors. Now thats my kind of core :) lol

[http://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB](http://ark.intel.com/products/33910/Intel-Core2-Duo-Processor-E8400-6M-Cache-3_00-GHz-1333-MHz-FSB)
Yes I have the broken pipe error also. I run upstart as default though. 
Whoa!! Wolfdales how appropriate for this cycle:D

---

### Post by ventrical on 2015-05-06
+1 :) lol

---

### Post by ventrical on 2015-05-06
> **runrickus said:**
> The Wolf Lives.
I have to remember to feed the good wolf..;)
```
inxi -b
System:    Host: me-Aspire-M3300 Kernel: 4.0.0-040000-lowlatency x86_64 (64 bit)
           Desktop: N/A Distro: Ubuntu 15.10 wily
Machine:   System: Acer product: Aspire M3300
           Mobo: Acer model: FRS780M
           Bios: American Megatrends v: P03-B0 date: 11/16/2009
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) speed/max: 800/2600 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Marvell 88E8071 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 2500.5GB (2.8% used)
Info:      Processes: 202 Uptime: 1:11 Memory: 725.9/5967.1MB
           Client: Shell (bash) inxi: 2.2.16 

```

@runrickus

I noticed that little program 'inxi' that you used and so I downloaded and installed. Wow .. is that ever handy.


here is another one of my boxes..
```

ventrical@ventrical-P5QL-PRO:~$ inxi -b
System:    Host: ventrical-P5QL-PRO Kernel: 3.19.0-15-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.0 Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5QL PRO v: Rev 1.xx
           Bios: American Megatrends v: 1004 date: 07/01/2009
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) speed/max: 1603/2403 MHz
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
           driver: ATL1E
Drives:    HDD Total Size: 120.0GB (9.9% used)
Info:      Processes: 175 Uptime: 26 min Memory: 623.7/2000.3MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-P5QL-PRO:~$ 

```

---

### Post by ventrical on 2015-05-06
Ok... just for fun I am going to try and do an upgrade to 15.10 ww on this overclocked single core P4@ near 5.0GHz.

```

ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-12-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.04 vivid
Machine:   Mobo: ASUSTeK model: P5AD2-E-Deluxe v: Rev 1.xx
           Bios: American Megatrends v: 1005.002 date: 01/19/2006
CPU:       Single core Intel Pentium 4 (-HT-) speed: 4998 MHz (max)
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 160.0GB (4.0% used)
Info:      Processes: 179 Uptime: 1 min Memory: 357.3/2000.7MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.58 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.60 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.59 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +34.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +26.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +11.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +41.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +2.0°C)
                       (emerg = +110.0°C, hyst = +10.0°C)


```

---

### Post by slickymaster on 2015-05-06
> **ventrical said:**
> @runrickus

I noticed that little program 'inxi' that you used and so I downloaded and installed. Wow .. is that ever handy.<...snip...>
[/CODE]
Xubuntu start seeding it from Utopic onward :p

Here's a quick HowTo on inxi, for those not familiarized with it: [Using inxi to detect hardware information]("http://xubuntu.org/news/inxi/")

---

### Post by QDR06VV9 on 2015-05-06
> **ventrical said:**
> @runrickus

I noticed that little program 'inxi' that you used and so I downloaded and installed. Wow .. is that ever handy.



I can't for the life of me remember who clued me into that a couple of years ago but thanks!
Yes it is  a handy little tool;)
Lots of options.
```
inxi -h
inxi supports the following options. You can combine them, or list them one
by one. Examples: inxi -v4 -c6 OR inxi -bDc 6. If you start inxi with no
arguments, it will show the short form.
 
The following options if used without -F, -b, or -v will show just option
line(s): A, C, D, G, I, M, N, P, R, S, f, i, m, n, o, p, l, u, r, s, t - you
can use these alone or together to show just the line(s) you want to see. If
you use them with -v [level], -b or -F, it will show the full output for that
line along with the output for the chosen verbosity level.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Output Control Options:
-A     Audio/sound card information.
-b     Basic output, short form. Like inxi -v 2, only minus hard disk names.
-c     Color schemes. Scheme number is required. Color selectors run a color
       selector option prior to inxi starting which lets you set the config
       file value for the selection.
       Supported color schemes: 0-32 Example: inxi -c 11
       Color selectors for each type display (NOTE: irc and global only show
       safe color set):
         94  Console, out of X
         95  Terminal, running in X - like xTerm
         96  Gui IRC, running in X - like Xchat, Quassel, Konversation etc.
         97  Console IRC running in X - like irssi in xTerm
         98  Console IRC not in  X
         99  Global - Overrides/removes all settings. Setting specific removes
             global. 
-C     CPU output, including per CPU clockspeed and max CPU speed (if
       available). 
-d     Optical drive data. Same as -Dd. See also -x and -xx.
-D     Full hard Disk info, not only model, ie: /dev/sda ST380817AS 80.0GB.
       See also -x and -xx. Disk total used percentage includes swap partition
       size(s). 
-f     All cpu flags, triggers -C. Not shown with -F to avoid spamming. ARM
       cpus show 'features'.
-F     Full output for inxi. Includes all Upper Case line letters, plus -s and
       -n. Does not show extra verbose options like -d -f -l -m -o -p -r -t -u
       -x 
-G     Graphic card information (card, display server type/version,
       resolution, glx renderer, version).
-i     Wan IP address, and shows local interfaces (requires ifconfig network
       tool). Same as -Nni. Not shown with -F for user security reasons, you
       shouldn't paste your local/wan IP.
-I     Information: processes, uptime, memory, irc client (or shell type),
       inxi version.
-l     Partition labels. Default: short partition -P. For full -p output, use:
       -pl (or -plu).
-m     Memory (RAM) data. Physical system memory array(s), capacity, how many
       devices (slots) supported, and individual memory devices (sticks of
       memory etc). For devices, shows device locator, size, speed, type
       (like: DDR3). Also see -x, -xx, -xxx
-M     Machine data. Motherboard, Bios, and if present, System Builder (Like
       Lenovo). Older systems/kernels without the required /sys data can use
       dmidecode instead, run as root. Dmidecode can be forced with -! 33
-n     Advanced Network card information. Same as -Nn. Shows interface, speed,
       mac id, state, etc.
-N     Network card information. With -x, shows PCI BusID, Port number.
-o     Unmounted partition information (includes UUID and LABEL if available).
       Shows file system type if you have file installed, if you are root OR
       if you have added to /etc/sudoers (sudo v. 1.7 or newer)
       Example: <username> ALL = NOPASSWD: /usr/bin/file  
-p     Full partition information (-P plus all other detected partitions).
-P     Basic partition information (shows what -v 4 would show, but without
       extra data). Shows, if detected: / /boot /home /tmp /usr /var. Use -p
       to see all mounted partitions.
-r     Distro repository data. Supported repo types: APT; PACMAN; PISI; YUM;
       URPMQ; Ports.
-R     RAID data. Shows RAID devices, states, levels, and components, and
       extra data with -x/-xx. md-raid: If device is resyncing, shows resync
       progress line as well.
-s     Sensors output (if sensors installed/configured): mobo/cpu/gpu temp;
       detected fan speeds. Gpu temp only for Fglrx/Nvidia drivers. Nvidia
       shows screen number for > 1 screens.
-S     System information: host name, kernel, desktop environment (if in X),
       distro 
-t     Processes. Requires extra options: c (cpu) m (memory) cm (cpu+memory).
       If followed by numbers 1-20, shows that number of processes for each
       type (default: 5; if in irc, max: 5): -t cm10
       Make sure to have no space between letters and numbers (-t cm10 -
       right, -t cm 10 - wrong).
-u     Partition UUIDs. Default: short partition -P. For full -p output, use:
       -pu (or -plu).
-v     Script verbosity levels. Verbosity level number is required. Should not
       be used with -b or -F
       Supported levels: 0-7 Example: inxi -v 4
         0   Short output, same as: inxi
         1   Basic verbose, -S + basic CPU + -G + basic Disk + -I.
         2   Networking card (-N), Machine (-M) data, shows basic hard disk
             data (names only), and, if present, basic raid (devices only, and
             if inactive, notes that). similar to: inxi -b
         3   Advanced CPU (-C), network (-n) data, and switches on -x advanced
             data option.
         4   Partition size/filled data (-P) for (if present): /, /home,
             /var/, /boot. Shows full disk data (-D).
         5   Audio card (-A); sensors (-s), memory/ram (-m), partition
             label (-l) and UUID (-u), short form of optical drives, standard
             raid data (-R).
         6   Full partition (-p), unmounted partition (-o), optical drive
             (-d), full raid; triggers -xx.
         7   Network IP data (-i); triggers -xxx.
-w     Local weather data/time. To check an alternate location, see:
       -W <location>. For extra weather data options see -x, -xx, and -xxx.
-W     <location> Supported options for <location>: postal code; city,
       state/country; latitude/longitude. Only use if you want the weather
       somewhere other than the machine running inxi. Use only ascii
       characters, replace spaces in city/state/country names with '+'.
       Example: inxi -W new+york,ny 
-x     Adds the following extra data (only works with verbose or line output,
       not short form):
         -C  CPU Flags, Bogomips on Cpu;
         -d  Extra optical drive data; adds rev version to optical drive.
         -D  Hdd temp with disk data if you have hddtemp installed, if you are
             root OR if you have added to /etc/sudoers (sudo v. 1.7 or newer)
             Example: <username> ALL = NOPASSWD: /usr/sbin/hddtemp 
         -G  Direct rendering status for Graphics (in X).
         -G  (for single gpu, nvidia driver) screen number gpu is running on.
         -i  IPv6 as well for LAN interface (IF) devices.
         -I  System GCC, default. With -xx, also show other installed GCC
             versions. If running in console, not in IRC client, shows shell
             version number, if detected. Init/RC Type and runlevel (if
             available). 
         -m  Part number; Max memory module size (if available).
      -N -A  Version/port(s)/driver version (if available) for Network/Audio;
   -N -A -G  Network, audio, graphics, shows PCI Bus ID/Usb ID number of card.
         -R  md-raid: Shows component raid id. Adds second RAID Info line:
             raid level; report on drives (like 5/5); blocks; chunk size;
             bitmap (if present). Resync line, shows blocks synced/total
             blocks. zfs-raid: Shows raid array full size; available size;
             portion allocated to RAID
         -S  Desktop toolkit if avaliable (GNOME/XFCE/KDE only); Kernel gcc
             version 
         -t  Memory use output to cpu (-xt c), and cpu use to memory (-xt m).
      -w -W  Wind speed and time zone (-w only).
-xx    Show extra, extra data (only works with verbose or line output, not
       short form):
         -A  Chip vendor:product ID for each audio device.
         -C  Minimum CPU speed, if available.
         -D  Disk serial number.
         -G  Chip vendor:product ID for each video card.
         -I  Other detected installed gcc versions (if present). System
             default runlevel. Adds parent program (or tty) for shell info if
             not in IRC (like Konsole or Gterm). Adds Init/RC (if found)
             version number.
         -m  Manufacturer, Serial Number, single/double bank (if found).
         -M  Chassis information, bios rom size (dmidecode only), if data for
             either is available.
         -N  Chip vendor:product ID for each nic.
         -R  md-raid: Superblock (if present); algorythm, U data. Adds system
             info line (kernel support,read ahead, raid events). If present,
             adds unused device line. Resync line, shows progress bar.
         -S  Display manager (dm) in desktop output, if in X (like kdm, gdm3,
             lightdm). 
      -w -W  Humidity, barometric pressure.
   -@ 11-14  Automatically uploads debugger data tar.gz file to
             ftp.techpatterns.com. EG: inxi -xx@14
-xxx   Show extra, extra, extra data (only works with verbose or line output,
       not short form):
         -m  Width of memory bus, data and total (if present and greater than
             data); Detail, if present, for Type; module voltage, if
             available. 
         -S  Panel/shell information in desktop output, if in X (like
             gnome-shell, cinnamon, mate-panel).
      -w -W  Location (uses -z/irc filter), weather observation time, wind
             chill, heat index, dew point (shows extra lines for data where
             relevant). 
-y     Required extra option: integer, 80 or greater. Set the output line
       width max. Overrides IRC/Terminal settings or actual widths. If used
       with -h, put -y option first. Example: inxi -y 130
-z     Security filters for IP/Mac addresses, location, user home directory
       name. Default on for irc clients.
-Z     Absolute override for output filters. Useful for debugging networking
       issues in irc for example.
 
Additional Options:
-h --help      This help menu.
-H             This help menu, plus developer options. Do not use dev options
               in normal operation!
--recommends   Checks inxi application dependencies + recommends, and
               directories, then shows what package(s) you need to install to
               add support for that feature.
-V --version   inxi version information. Prints information then exits.
 
Debugging Options:
-%     Overrides defective or corrupted data.
-@     Triggers debugger output. Requires debugging level 1-14 (8-10 - logging
       of data). Less than 8 just triggers inxi debugger output on screen.
         1-7 On screen debugger output
         8   Basic logging
         9   Full file/sys info logging
         10  Color logging.
       The following create a tar.gz file of system data, plus collecting the
       inxi output to file. To automatically upload debugger data tar.gz file
       to ftp.techpatterns.com: inxi -xx@ <11-14>
       For alternate ftp upload locations:
       Example: inxi -! ftp.yourserver.com/incoming -xx@ 14 
         11  With data file of xiin read of /sys.
         12  With xorg conf and log data, xrandr, xprop, xdpyinfo, glxinfo etc.
         13  With data from dev, disks, partitions, etc., plus xiin data file.
         14  Everything, full data collection.
 
Advanced Options:
-! 31  Turns off hostname in output. Useful if showing output from servers etc.
-! 32  Turns on hostname in output. Overrides global B_SHOW_HOST='false'
-! 33  Forces use of dmidecode data instead of /sys where relevant (-M).

```
Have you been able to overclock the wolfdales?

---

### Post by grahammechanical on 2015-05-06
inxi?

[https://code.google.com/p/inxi/wiki/Installation](https://code.google.com/p/inxi/wiki/Installation)

> The following extra packages will be installed:
  gawk hddtemp libsigsegv2 lm-sensors mesa-utils
Suggested packages:
  gawk-doc ksensors fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed
  gawk hddtemp inxi libsigsegv2 lm-sensors mesa-utils

That is what we get on wily. And this is the result i get.

> graham@sdb1-Uplus1:~$ inxi -b
System:    Host: sdb1-Uplus1 Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5B-Deluxe v: Rev 1.xx
           Bios: American Megatrends v: 1004 date: 01/22/2007
CPU:       Dual core Intel Core2 6600 (-MCP-) speed/max: 1596/2394 MHz
Graphics:  Card: NVIDIA GT216 [GeForce GT 220]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.1hz
           GLX Renderer: GeForce GT 220/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 304.125
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller
           driver: sky2
           Card-2: Marvell 88E8001 Gigabit Ethernet Controller driver: skge
           Card-3: Realtek RTL8187 Wireless Adapter driver: rtl8187
Drives:    HDD Total Size: 750.1GB (1.5% used)
Info:      Processes: 180 Uptime: 1:43 Memory: 672.6/992.4MB
           Client: Shell (bash) inxi: 2.2.16 

Regards.

---

### Post by ventrical on 2015-05-06
> **runrickus said:**
> I can't for the life of me remember who clued me into that a couple of years ago but thanks!

Have you been able to overclock the wolfdales?

Yes I have . Currently I have a geometry problem with setting up the right cooler for them. I only have one CoolerMaster Air that fits all my various boards. I have other air compressors but they are either too big or will not seat correctly. Even though the lithography of the Wolfdales is 45nm they are very touchy to voltage/freq increases and respond by generating heat very rapidly so the cooler has to be seated just right . I am working on that. :)

Thanks for other info on inxi! :)

Regards..

---

### Post by ventrical on 2015-05-06
> **grahammechanical said:**
> inxi?

[https://code.google.com/p/inxi/wiki/Installation](https://code.google.com/p/inxi/wiki/Installation)



That is what we get on wily. And this is the result i get.



Regards.

Yes grahammechanical .. I just seen that. Looks like some kewl tools have been held back for a few cycles.

Here is results from one of my OC boxes.  Unity has problems with frequencies over 5GHz so I had to lower the freq. Anyways it proves that even older machines can run Unity with the right graphics adapter. For a single core it is running very fast and using only 677MHz memory.

```

ventrical@ventrical-System-Product-Name:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily
ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-12-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5AD2-E-Deluxe v: Rev 1.xx
           Bios: American Megatrends v: 1005.002 date: 01/19/2006
CPU:       Single core Intel Pentium 4 (-HT-) speed: 4647 MHz (max)
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 160.0GB (4.5% used)
Info:      Processes: 176 Uptime: 33 min Memory: 595.6/2000.7MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-System-Product-Name:~$ 

```

I am going to try with my xubuntu install as it is usually more stable at higher speeds.

regards..

---

### Post by QDR06VV9 on 2015-05-06
> **ventrical said:**
> Yes I have . Currently I have a geometry problem with setting up the right cooler for them. I only have one CoolerMaster Air that fits all my various boards. I have other air compressors but they are either too big or will not seat correctly. Even though the lithography of the Wolfdales is 45nm _**they are very touchy to voltage/freq increases and respond by generating heat very rapidly so the cooler has to be seated just right**_ . I am working on that. :)

Thanks for other info on inxi! :)

Regards..
Thats what I was curious about.Thanks
Kind Regards

---

### Post by slickymaster on 2015-05-06
> **ventrical said:**
> ...
I am going to try with my xubuntu install as it is usually more stable at higher speeds.
...
And with Xubuntu you'll get [this]("http://ubuntuforums.org/showthread.php?t=2276829&p=13279943&viewfull=1#post13279943"). ;)

---

### Post by Cavsfan on 2015-05-06
I'm in. Fabricated another 10GB partition so I could keep Vivid Mate for a while. I had to do a live cd and move part of my space across from the physical partitions to the extended partitions. 
I can thank Drs305 for teaching me how to do that!
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
NAME="Ubuntu"
VERSION="15.10 (Wily Werewolf)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu Wily Werewolf (development branch)"
VERSION_ID="15.10"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

I installed a Ubuntu with Unity from 15.04 and then before updating anything I did the **sudo sed -i 's/vivid/wily/g' /etc/apt/sources.list**
from ventrical's signature link [https://wiki.ubuntu.com/U%2B1/tester-wiki#preview](https://wiki.ubuntu.com/U%2B1/tester-wiki#preview)

Is  it really neccessary to edit that **/usr/share/python-apt/templates/Ubuntu.info** file?
I did it for Vivid but is it really needed?

---

### Post by xeizoo on 2015-05-06
Only if you don't want Synaptics repositories gui to crash ...

---

### Post by xc3RnbFO8P on 2015-05-06
Me and Zika  are here to help you guys, just ask if you need help :p
> ringi@ringi-Lenovo-Ideapad-Flex-15:~$ inxi -b
System:    Host: ringi-Lenovo-Ideapad-Flex-15 Kernel: 3.19.0-16-generic i686 (32 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   System: LENOVO product: 20309 v: Lenovo Ideapad Flex 15
           Mobo: LENOVO model: Strawberry 5D v: 31900003Std
           Bios: LENOVO v: 8ACN07WW date: 07/31/2013
CPU:       Dual core Intel Core i3-4010U (-HT-MCP-) speed/max: 1698/1700 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller
           Display Server: X.Org 1.17.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.0hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile x86/MMX/SSE2
           GLX Version: 3.0 Mesa 10.5.2
Network:   Card-1: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           driver: r8169
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
           Card-3: Atheros
Drives:    HDD Total Size: 500.1GB (6.1% used)
Info:      Processes: 232 Uptime: 10:12 Memory: 1946.7/3767.4MB
           Client: Shell (bash) inxi: 2.2.16 

---

### Post by slickymaster on 2015-05-06
> **Cavsfan said:**
> ...
Is  it really neccessary to edit that **/usr/share/python-apt/templates/Ubuntu.info** file?
I did it for Vivid but is it really needed?
If you come to face [this issue]("https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work") with your Software & Updates, yes.

---

### Post by QDR06VV9 on 2015-05-06
> **slickymaster said:**
> If you come to face [this issue]("https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work") with your Software & Updates, yes.

+1
I would be rather surprised if he has'nt already.
plus this just rolled in for me
```
The following packages will be upgraded:
  aspell debianutils dictionaries-common dmidecode geoip-database
  glib-networking glib-networking-common glib-networking-services inputattach
  intltool-debian krb5-locales libabw-0.1-1 libaspell15 libbabl-0.1-0
  libcap-dev libcap-ng0 libcap2 libcap2-bin libcdr-0.1-1 libcloog-isl4
  libcommon-sense-perl libdatrie1 libdjvulibre-text libdjvulibre21
  libdouble-conversion1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2
  libe-book-0.1-1 libevdev2 libfile-fcntllock-perl libgexiv2-2
  libgssapi-krb5-2 libgusb2 libharfbuzz-dev libharfbuzz-gobject0
  libharfbuzz-icu0 libharfbuzz0b libimlib2 libisl13 libk5crypto3 libkrb5-3
  libkrb5support0 liblouis-data liblouis2 libmodule-signature-perl
  libmspub-0.1-1 libmwaw-0.3-3 libnet-domain-tld-perl libodfgen-0.1-1
  libp11-kit0 libpciaccess0 libpkcs11-helper1 librevenge-0.0-0 librtmp1
  libvdpau1 libvisio-0.1-1 libwps-0.3-3 libxdmcp-dev libxdmcp6 libxshmfence1
  libxxf86vm1 p11-kit p11-kit-modules po-debconf python-urllib3 python3-louis
  python3-pyatspi python3-urllib3 rtmpdump ssl-cert usb-modeswitch-data
73 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.5 MB of archives.
After this operation, 524 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

Regards

---

### Post by Cavsfan on 2015-05-06
Ok, thanks!

I was experiencing some issues. I was messing with CCSM and it kept blowing me back to the login screen but it looks like the file has been fixed, or has it?
At the top it has devel, then wiley, then vivid etc. Should I delete the devel stuff out of it or is is good?

This just goes from the top to where it starts with vivid:
```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 15.10 'Wily Werewolf'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: wily
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 15.10 'Wily Werewolf'

Suite: wily
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*15.10
MatchURI: cdrom:\[Ubuntu.*15.10
Description: Cdrom with Ubuntu 15.10 'Wily Werewolf'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: wily-security
ParentSuite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: wily-security
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb
Description: Recommended updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb
Description: Pre-released updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb
Description: Unsupported updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: vivid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
```

Thanks! I am amazed at how guick the developers got this up!

---

### Post by QDR06VV9 on 2015-05-06
I'm just guessing here but I think Ventrical runs that very same set-up
I tend to be A little less brave with mine.

```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.10 'wily Vervet'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: wily
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.10 'wily Vervet'

Suite: wily
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.
MatchURI: cdrom:\[Ubuntu.*14.10
Description: Cdrom with Ubuntu 14.10 'wily Vervet'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: wily-security
ParentSuite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: wily-security
ParentSuite:wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb
Description: Recommended updates

Suite:wily-updates
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb
Description: Pre-released updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb
Description: Unsupported updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports

```
That is a good question though, And I don't confess to have the right answer.
Kind Regards

---

### Post by ventrical on 2015-05-06
> **Cavsfan said:**
> Ok, thanks!

I was experiencing some issues. I was messing with CCSM and it kept blowing me back to the login screen but it looks like the file has been fixed, or has it?
At the top it has devel, then wiley, then vivid etc. Should I delete the devel stuff out of it or is is good?

This just goes from the top to where it starts with vivid:
```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 15.10 'Wily Werewolf'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: wily
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 15.10 'Wily Werewolf'

Suite: wily
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*15.10
MatchURI: cdrom:\[Ubuntu.*15.10
Description: Cdrom with Ubuntu 15.10 'Wily Werewolf'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: wily-security
ParentSuite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: wily-security
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb
Description: Recommended updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb
Description: Pre-released updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb
Description: Unsupported updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: vivid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
```

Thanks! I am amazed at how guick the developers got this up!

The wily suite has to be on top of the /devel/ as per pointed out by zika the last cycle. But looks like it is working there.:)

Regards

---

### Post by Cavsfan on 2015-05-06
> **runrickus said:**
> I'm just guessing here but I think Ventrical runs that very same set-up
I tend to be A little less brave with mine.

```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.10 'wily Vervet'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: wily
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.10 'wily Vervet'

Suite: wily
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.
MatchURI: cdrom:\[Ubuntu.*14.10
Description: Cdrom with Ubuntu 14.10 'wily Vervet'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: wily-security
ParentSuite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: wily-security
ParentSuite:wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb
Description: Recommended updates

Suite:wily-updates
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb
Description: Pre-released updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb
Description: Unsupported updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports

```
That is a good question though, And I don't confess to have the right answer.
Kind Regards

Thanks! I took out the devel stuff and rebooted. It seems to like it. :popcorn:

---

### Post by ventrical on 2015-05-06
Just for general purpose info .. I finally was able to get unity to run stable above 5.0GHz (as which is the machine I am on now.) I know this is off topic so I will leave overclocking info on another forum that I created.

```

ventrical@ventrical-System-Product-Name:~$ inxi -b
System:    Host: ventrical-System-Product-Name Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   Mobo: ASUSTeK model: P5AD2-E-Deluxe v: Rev 1.xx
           Bios: American Megatrends v: 1005.002 date: 01/19/2006
CPU:       Single core Intel Celeron D (-UP-) speed: 5051 MHz (max)
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Gallium 0.4 on NV98 GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 160.0GB (4.5% used)
Info:      Processes: 179 Uptime: 1 min Memory: 373.1/2000.6MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.58 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.60 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.61 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.20 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4066 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +26.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +29.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:   +0.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +50.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +2.0°C)
                       (emerg = +110.0°C, hyst = +10.0°C)

ventrical@ventrical-System-Product-Name:~$ 

ventrical@ventrical-System-Product-Name:~$ sudo dmidecode -t processor | grep "Speed"
[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 5051 MHz
ventrical@ventrical-System-Product-Name:~$ 

```

Regards..

---

### Post by QDR06VV9 on 2015-05-06
@cavsfan nice! ;)
@ventrical I can see your power meter spinning like a top LOL That's a nice chip!

---

### Post by ventrical on 2015-05-06
> **runrickus said:**
> @cavsfan nice! ;)
@ventrical I can see your power meter spinning like a top LOL That's a nice chip!

Thanks .... Wolfdale is next ! :) I have a 'howler' that has oversized pins so I am going to hack it and try to set these smaller pins that fit with the bottom plate into it and then I'll hack the werewolf :) lol  Oy!!! Just remebered .. I am using ARTIC SILVER paste... hmmm.. wonder if that will affect performance :) lol

Regards..

---

### Post by Cavsfan on 2015-05-06
@         runrickus - thank for answering my question. :)

@         ventrical - with such a ripping processor why the old video card? You should have a Geforce 780ti or better. :)
My son has that card with an i7-4790K processor which he has been able to get to 4.2Ghz and a 4k monitor to boot.

But, on topic (sort of) I was using gedit and needed to have the lines not wrap at the end but gedit does not have preferences for which to change this or display line numbers.
I had to use leafpad. So, that is odd that the preferences are missing from gedit.

---

### Post by QDR06VV9 on 2015-05-06
> **ventrical said:**
> Thanks .... Wolfdale is next ! :) I have a 'howler' that has oversized pins so I am going to hack it and try to set these smaller pins that fit with the bottom plate into it and then I'll hack the werewolf :) lol  Oy!!! Just remebered .. I am using ARTIC SILVER paste... hmmm.. wonder if that will affect performance :) lol

Regards..

I have not seen any evidence that the color of the paste maters I ran all kinds of tests when I heard that artic tsilver would or could get hot enough to split a CPU. But the amount used seemed to be important.
So once again moderation is key. Too much can be BAD.
I would be curious to see if you agree.Can not wait to see the wolfdales gobbling power though.
I'm Using ARTIC SILIVER on this rig as we post!
Regards
> [COLOR=#070F14][FONT=Verdana]Your choice pf  thermal paste won't have a noticeable difference on temps when you are  deciding between two top brands/compounds like the ones you mentioned,  so go for a mid-range (pricewise) solution.[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]However do not go for cheap (unbranded) ones as they will let you down in terms of thermal conductivity and wear and tear.[/FONT][/COLOR]
From here [http://www.tomshardware.com/forum/322131-28-best-thermal-compound](http://www.tomshardware.com/forum/322131-28-best-thermal-compound)

---

### Post by Hazzabin on 2015-05-06
No way I could let all you 'Wolfdales' have all the fun, so decided to jump in boots and all

> hazzauni1504@hazzauni1504:~$ inxi -bSystem:    Host: hazzauni1504 Kernel: 3.19.0-16-generic x86_64 (64 bit)
           Desktop: Unity 7.3.2  Distro: Ubuntu 15.10 wily
Machine:   System: ASUS product: All Series
           Mobo: ASUSTeK model: H81M-E v: Rev X.0x
           Bios: American Megatrends v: 0809 date: 01/22/2014
CPU:       Dual core Intel Core i3-4160 (-HT-MCP-) speed: 3600 MHz (max)
Graphics:  Card: Intel 4th Generation Core Processor Family Integrated Graphics Controller
           Display Server: X.Org 1.17.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: Mesa DRI Intel Haswell GLX Version: 3.0 Mesa 10.5.2
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1500.3GB (1.1% used)
Info:      Processes: 212 Uptime: 3 min Memory: 1328.6/3824.8MB
           Client: Shell (bash) inxi: 2.2.16 




---

### Post by ventrical on 2015-05-06
> **runrickus said:**
> I have not seen any evidence that the color of the paste maters I ran all kinds of tests when I heard that artic tsilver would or could get hot enough to split a CPU. But the amount used seemed to be important.
So once again moderation is key. Too much can be BAD.
I would be curious to see if you agree.Can not wait to see the wolfdales gobbling power though.
I'm Using ARTIC SILIVER on this rig as we post!
Regards

From here [http://www.tomshardware.com/forum/322131-28-best-thermal-compound](http://www.tomshardware.com/forum/322131-28-best-thermal-compound)

:) ... uhhh .. I meant  Silver as in Silver Bullet , werewolf ? ya know the old story.... :) lol

  No .. really .. thanks for the added info. Much appreciated.:)

Regards..

---

### Post by ventrical on 2015-05-06
> **Cavsfan said:**
> @         runrickus - thank for answering my question. :)

@         ventrical - with such a ripping processor why the old video card? You should have a Geforce 780ti or better. :)
My son has that card with an i7-4790K processor which he has been able to get to 4.2Ghz and a 4k monitor to boot.

But, on topic (sort of) I was using gedit and needed to have the lines not wrap at the end but gedit does not have preferences for which to change this or display line numbers.
I had to use leafpad. So, that is odd that the preferences are missing from gedit.

The Celeron D is circa 2006 and only single core. The wolfdale is dual core and yes .. it is suppossed to be a rip but the adapter card has to match ... it's .. how can I say .. very touchy .. so sometimes older cards work better for any particular processor. But I have taken note of what you posted and may eventually have to invest in newer nVidia devices regardless.

Thanks again.

Regards..

---

### Post by pixelro on 2015-05-06
\o/ so many werewolves

---

### Post by Hazzabin on 2015-05-07
Installed into both Ubuntu 15.04 Unity and Ubuntu Mate, both over the pass few hours have been running nicely, I must mention I do not have any additional 

graphic cards other than the graphics whats on my Motherboard.

---

### Post by QDR06VV9 on 2015-05-07
> **ventrical said:**
> :) ... uhhh .. I meant  Silver as in Silver Bullet , werewolf ? ya know the old story.... :) lol

  No .. really .. thanks for the added info. Much appreciated.:)

Regards..
It must have been a Full Moon last night.LOL
Whoops got a little carried away didn't I!!:oops:
Because I know full well you are very skilled with products and hardware.
Some times I have to stand on my tip toes so It won't go over my head.):P

---

### Post by Cavsfan on 2015-05-07
@ventrical, I forgot to mention that my son said the K at the end of for example i7-4790[COLOR=#ff0000]K[/COLOR] processor means that it is meant to overclock.
He just does it in bios and it's easy he said. He tried to take it to 4.5GB and it blue screened on him - lol one of those things windows does. :lol:

Gedit - where'd the preferences go? It's unusable for some tasks as it is.

---

### Post by fjgaude on 2015-05-07
> **Cavsfan said:**
> @         runrickus - thank for answering my question. :)

@         ventrical - with such a ripping processor why the old video card? You should have a Geforce 780ti or better. :)
My son has that card with an i7-4790K processor which he has been able to get to 4.2Ghz and a 4k monitor to boot.

But, on topic (sort of) I was using gedit and needed to have the lines not wrap at the end but gedit does not have preferences for which to change this or display line numbers.
I had to use leafpad. So, that is odd that the preferences are missing from gedit.

Say, this is off- topic but you tell if Ubuntu is ready for 4K monitors?

Thanks!

---

### Post by xeizoo on 2015-05-08
Wily works great so far, exciting knowing breakage will come, particularly for us with Nvidia graphics ....

On the OC subtopic earlier, I did some busclock as Haswell permits it and if the RAM can handle it, 6.5% extra is stable for me which gives a Turbo-frequency of 3.83GHz and memory runs at 2133MHz. I do have a lower power S-spec CPU(max TDP=65W) but if it can be clocked it will be clocked  ;-) 

> per@z87a-4570s:~$ inxi -bSystem:    Host: z87a-4570s Kernel: 4.0.1-040001-lowlatency x86_64 (64 bit)
           Desktop: Gnome 3.14.4 Distro: Ubuntu 15.10 wily
Machine:   System: ASUS product: All Series
           Mobo: ASUSTeK model: Z87-A v: Rev 1.xx
           Bios: American Megatrends v: 2103 date: 08/15/2014
CPU:       Quad core Intel Core i5-4570S (-MCP-) speed/max: 2900/3600 MHz
Graphics:  Card: NVIDIA GK104 [GeForce GTX 680]
           Display Server: X.Org 1.17.1 driver: nvidia
           Resolution: 2560x1440@60.0hz
           GLX Renderer: GeForce GTX 680/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 349.16
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 6281.3GB (49.5% used)
Info:      Processes: 232 Uptime: 1 day Memory: 1803.4/7921.9MB
           Client: Shell (bash) inxi: 2.2.16


---

### Post by ventrical on 2015-05-08
> **runrickus said:**
> It must have been a Full Moon last night.LOL
Whoops got a little carried away didn't I!!:oops:
Because I know full well you are very skilled with products and hardware.
Some times I have to stand on my tip toes so It won't go over my head.):P

We had a full moon for three days around here. I could feel it, it was so strong. I had a ravenous appetite, could hear better, my ears felt furry and I had this strange compulsion to howl and run with the wolf pack like Mogli did in Kipling's  The Jungle Book . :)lol

Regards

---

### Post by slickymaster on 2015-05-08
> **runrickus said:**
> It must have been a Full Moon last night.LOL
Whoops got a little carried away didn't I!!:oops:
Because I know full well you are very skilled with products and hardware.
Some times I have to stand on my tip toes so It won't go over my head.):P
> **ventrical said:**
> We had a full moon for three days around here. I could feel it, it was so strong. I had a ravenous appetite, could hear better, my ears felt furry and I had this strange compulsion to howl and run with the wolf pack like Mogli did in Kipling's  The Jungle Book . :)lol

Regards
Guys, let's keep the thread on topic, please.

---

### Post by Cavsfan on 2015-05-08
> **fjgaude said:**
> Say, this is off- topic but you tell if Ubuntu is ready for 4K monitors?

Thanks!

My son told me that in order to get true 4k on his monitor he would have to have another GeForce GTX 780 ti card and run them in SLI mode.

He also only has windows 8.1 which uses directx 11. Windows 10 will have directx 12. I don't believe there is a way to use that on Ubuntu. But, I'm not a gamer.

Edit: sorry I didn't see the previous post.

---

### Post by Ian_Worrall on 2015-05-08
> **Cavsfan said:**
> My son told me that in order to get true 4k on his monitor he would have to have another GeForce GTX 780 ti card and run them in SLI mode.

He also only has windows 8.1 which uses directx 11. Windows 10 will have directx 12. I don't believe there is a way to use that on Ubuntu. But, I'm not a gamer.

Edit: sorry I didn't see the previous post.

Quick answer: DX12 is Windows 10 only. The Linux equivalent will be "Vulkan", which was only launched a few weeks ago.

---

