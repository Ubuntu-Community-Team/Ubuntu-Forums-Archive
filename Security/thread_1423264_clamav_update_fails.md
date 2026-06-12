---
title: "clamav update fails"
date: 2010-03-06
forum: Security
---

### Post by dgermann on 2010-03-06
Hi--

I am running 8.04 lts. Today I got an update manager request to update clamav and got errors from doing it. So I tried this:
```
doug@doug2:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up clamav-freshclam (0.95.3+dfsg-1ubuntu0.09.04~hardy2.2) ...
chown: invalid user: `clamav:adm'
dpkg: error processing clamav-freshclam (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-freshclam
 clamav
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
doug@doug2:~$ 

```

That invalid user thing seems a clue, but I do not know what to do with it.

Running the same on another computer, I did not receive any errors.

What do I do next?

Thanks!

---

### Post by adam814 on 2010-03-07
Try this:
```
sudo apt-get remove clamav-data clamav-freshclam clamav && sudo apt-get install clamav clamav-data clamav-freshclam
```

---

### Post by dgermann on 2010-03-07
adam814--

Thanks!

I had thought of doing that through synaptic, but paused, thinking there might be something else to try.

I did as you suggested:
```
doug@doug2:~$ sudo apt-get remove clamav-data clamav-freshclam clamav && sudo apt-get install clamav clamav-data clamav-freshclam
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clamav-data is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libdate-calc-perl clamav-base libcarp-clan-perl libclamav6
  libfile-find-rule-perl libconfig-tiny-perl libnumber-compare-perl
  libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  clamav clamav-daemon clamav-freshclam clamtk
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 2445kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 266312 files and directories currently installed.)
Removing clamtk ...
Removing clamav ...
Removing clamav-daemon ...
Removing clamav-freshclam ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  clamav-data: Conflicts: clamav-freshclam but 0.95.3+dfsg-1ubuntu0.09.04~hardy2.2 is to be installed
  clamav-freshclam: Conflicts: clamav-data
E: Broken packages
doug@doug2:~$ 

```

I see these as clues: the libclamav6 and the clamav-base it suggests autoremoving; and conflict with freshclam with clamav-data. What do you suppose that means?

So I ran the autoremove and then:
> doug@doug2:~$ sudo apt-get install clamav clamav-data clamav-freshclam clamtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  clamav-data: Conflicts: clamav-freshclam but 0.95.3+dfsg-1ubuntu0.09.04~hardy2.2 is to be installed
  clamav-freshclam: Conflicts: clamav-data
E: Broken packages
doug@doug2:~$ 


I updated another computer I have this afternoon for clamav, and it went without a problem. So it seems to be just this computer.

Any ideas?

Thanks, adam814!

---

### Post by adam814 on 2010-03-07
Hrmm...tried "apt-get install -f" yet?  Sometimes that works out dependencies.  Otherwise I'd try the last install command you did but without explicitly installing clamav-data.

---

### Post by dgermann on 2010-03-07
Hi--

I may have found the answer: I purged all the clamav apps I had, then reinstalled them.

It seems to have choked when I installed clamtk, so I had to purge it all, and then install all but clamtk, then clamtk separately, and all went well.

I got the main clue from here: [https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/382265]("https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/382265"): "The purge/reinstall cycle is the correct fix."

I had tried the -f switch before I posted here the first time. No go.

Thanks for your help, adam814!

---

