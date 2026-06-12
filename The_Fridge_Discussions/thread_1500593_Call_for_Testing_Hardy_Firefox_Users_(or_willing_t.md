---
title: "Call for Testing: Hardy Firefox Users (or willing to install Hardy in a VM)"
date: 2010-06-03
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-06-03
**Background**

 Firefox 3.0 and xulrunner 1.9 are now unsupported by Mozilla. Rather than backporting security fixes to these now, we are moving to a support model where we will be introducing major new upstream versions in stable releases. The reason for this is [the support periods from Mozilla are gradually becoming shorter]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel"), and it will be more and more difficult for us to maintain our current support model in the future.

 **What we are going to do**

 We are going to release Firefox 3.6.4 as a minor update to the 3.6 series in Lucid. This will also be rolled out to Hardy, Jaunty and Karmic (along with xulrunner 1.9.2.4). The update for Lucid is quite trivial, but the update in Hardy, Jaunty and Karmic is not quite as simple.

 Before releasing these updates to the public, we need testing in Firefox, the extensions in the archive and distributions upgrades after those updates. We have published all these packages in a [PPA]("https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa") and we will track test results before moving anything to the archive.

 **How you can help**

 We need people running *Hardy* (Jaunty and Karmic will see a similar call for testing in the following days) in bare metal or a **virtual machine**. If you are willing to help, you can follow the instructions below:

 
[LIST=1] 
[*]Add the Mozilla Security PPA to your software sources You need to manually edit your /etc/apt/sources.list and add the following lines:

 deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) hardy main
 
 deb-src [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) hardy main 

  After saving the file, you have to run:

 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
 
 sudo apt-get update
 
 sudo apt-get dist-upgrade

 
[*]You have to have an account in our tracking system. Go to [http://mozilla.qa.ubuntu.com](http://mozilla.qa.ubuntu.com) and click on &#8220;Log In&#8221; and &#8220;Create New Account&#8221; 
[*]Explore your Firefox installation Basically we want people to perform the same activities that the do daily, without issues. In order to make testing easier, this is a checklist of things worth looking: 


[LIST] 
[*]The upgrade to Firefox 3.6.4 goes smoothly. 
[*]The extensions get upgraded as well. 
[*]All the Firefox plugins (i.e. Flash, Java) still work. 
[*]The extensions work correctly. 
[*]Full distributions upgrades are not broken. 
[*]Upgrades work with only the security pocket enabled (ie, hardy-updates disabled) 
[/LIST]
  
[/LIST]
 To report your findings you need to use the [test tracker]("http://mozilla.qa.ubuntu.com").

 Once you have selected the Hardy image, you will see a set of &#8220;testcases&#8221;, with a summary of how many reports have been sent. Obviously, the most important one is &#8220;Firefox&#8221;. 

 [IMG]http://ubuntutesting.files.wordpress.com/2010/06/list.png?w=490[/IMG]

 Once you open one of the testcases, you will be able to report back your findings if something went wrong. Even if everything went fine, it is always good to report back the success (&#8220;Passed&#8221;) with a comment on the activities you performed. 

 [IMG]http://ubuntutesting.files.wordpress.com/2010/06/testcase.png?w=490[/IMG]

 Use the &#8220;Firefox&#8221; testcase for general testing (upgrade, rendering, plugins, etc.) and the rest of the testcases if you want to report something more specific (Upgrades to Lucid, specific extensions errors, etc.)

 **IMPORTANT!! How to file bugs**

 As we are testing a PPA, not an official Ubuntu package, if you find an issue is NOT OK to file a bug in Launchpad. Rather than doing so, please, just explain your issue in the Comments field of the tracker and mark the test as Failed.

 The tracker requires a bug number in order to mark a test as Failed. To bypass this requirement, just use the bug number &#8220;1&#8243; [IMG]http://s.wordpress.com/wp-includes/images/smilies/icon_wink.gif[/IMG] 

 Thanks for helping to maintain secured Ubuntu stable releases! 

 Originally posted [here]("http://ubuntutesting.wordpress.com/2010/06/01/call-for-testing-firefox/") by Ara Pulido on Tue, June 1, 2010

 

[More...](http://fridge.ubuntu.com/node/2052)

---

### Post by kingcharles1666 on 2010-06-04
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
does not seem to work:

mico@ubuntu64:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 7EBC211F
gpg: requesting key 7EBC211F from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by kingcharles1666 on 2010-06-04
Downloading it manually and importing using synaptic worked ok:

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA6DCF7707EBC211F](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA6DCF7707EBC211F)

problem solved

---

