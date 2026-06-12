---
title: "elementary os luna - held packages error, interrupted upgrade"
date: 2016-05-15
forum: Ubuntu/Debian BASED
---

### Post by kakar on 2016-05-15
Hi,

I have elementary os luna installed on my laptop, which is based on 12.04 (32 bit). Recently, as I was making a system update, something went wrong with my battery and my laptop cutaway and turned off right in the middle of apt-get upgrade. When I restarted it later on, and tried to run update, I am getting the following error. I have tried the common suggestions found on this and other forums.

```


Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:


The following packages have unmet dependencies:
 
dpkg : Breaks: cups (< 1.7.5-10~) but 1.5.3-0ubuntu8.7 is to be installed


libfolks25 : Breaks: libfolks-eds25 (< 0.8.0-2~) but 0.6.8-2 is to be installed


libpango-1.0-0 : Breaks: plymouth (< 0.8.3-19) but 0.8.2-2ubuntu31.1 is to be installed


python-gi : Breaks: python-aptdaemon (< 1.0) but 0.43+bzr805-0ubuntu10 is to be installed


W: Unknown Multi-Arch type 'no' for package 'compiz-core'


W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'


W: You may want to run apt-get update to correct these problems


E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. 



```


[COLOR=#333333][FONT=Ubuntu]dpkg --get-selections | grep hold comes up empty, so I have no held packages. I tried autoremove with purge. I followed the whole procedure down to apt-get -f install, etc. 

Please help. Cheers![/FONT][/COLOR]

---

