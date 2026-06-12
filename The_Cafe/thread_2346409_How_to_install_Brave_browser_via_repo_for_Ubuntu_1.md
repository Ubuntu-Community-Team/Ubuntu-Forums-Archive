---
title: "How to install Brave browser via repo for Ubuntu 14.04 - 16.04"
date: 2016-12-14
forum: The Cafe
---

### Post by SeanKD on 2016-12-14
The new Brave browser ( [https://brave.com](https://brave.com) ), based on Chromium, is garnering a lot of interest lately. It is only available for amd64 currently. You can download the 64-bit deb file and install it, but this will not keep your Brave installation updated. Brave has a repo that can be added to your sources, but their instructions on adding it are borked and do not work. So, I decided to provide corrected instructions on adding the repo to the sources list so that you can install Brave and keep it updated. The instructions are as follows:

*IMPORTANT* Brave is only offered for the amd64 arch.

*NOTE* When I originally made this post, I inadvertently made an error. The code read 'sudo install brave' when it should have read 'sudo apt install brave'. The error has been corrected.

First, we need to download the repo keys and add them to the keyring:
```
wget -qO - https://s3-us-west-2.amazonaws.com/brave-apt/keys.asc | sudo apt-key add -
```
Second, we need to add the repo. **NOTE** If you're running 14.04 <= Ubuntu < 16.04 then change 'xenial' in the following line to 'trusty'
```
sudo add-apt-repository "deb [arch=amd64] https://s3-us-west-2.amazonaws.com/brave-apt xenial main"
```
The '[arch=amd64]' in the line above is to prevent apt from whining that it cannot find repo files for the i386 arch if your system is multiarch (i.e. you have added the i386 architecture).

Next, we need to update our sources.
```
sudo apt update
```
And finally, intall Brave
```
sudo apt install brave
```

That's it. Enjoy!

---

### Post by happydog500 on 2016-12-15
Nice Job, doesn't work. Says this;

> @Linux:~$ sudo install brave
install: missing destination file operand after ‘brave’
Try 'install --help' for more information.
roger@Linux:~$ sudo install brave
install: missing destination file operand after ‘brave’


 Hope adding a repo key and repo without anything else doesn't have any other negative effects. I downloaded from the site last time and it worked fine. 

Chris.

---

### Post by QIII on 2016-12-15
That should be

```
sudo apt install brave
```

---

### Post by SeanKD on 2016-12-15
Thanks for the proofreading! Correcting it now.

It was a typo on my part. It should be 'sudo apt install brave'. I have corrected it. Thanks for catching the error!

> **happydog500 said:**
> Nice Job, doesn't work. Says this;



 Hope adding a repo key and repo without anything else doesn't have any other negative effects. I downloaded from the site last time and it worked fine. 

Chris.

The error was caused by a typo on my part. It should read 'sudo apt install brave', not 'sudo install brave'. There aren't any negative effects from adding a repo and keys and both can easily be removed by opening Software&Updates if you feel so inclined.

---

### Post by rekram on 2017-07-07
That is a huge help!  I'm a complete newb to Ubuntu and appreciate you taking the time to lay this out step-by-step.  The install went off without a hitch.

My next goal is to try to figure out what any of what I pasted into the terminal means.  That is some freaky foreign language looking stuff and I'm happy to dive in.  

Thanks again for doing this.

---

