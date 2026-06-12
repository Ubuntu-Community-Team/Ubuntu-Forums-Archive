---
title: "Deleted Keyring default passwords and lost Internet connection"
date: 2011-04-29
forum: Security
---

### Post by panderohit on 2011-04-29
Hi

I was browsing too see if there was a disable function for the annoying keyring default prompt that I was asked for thrice during each boot of ubuntu 10.10. I adopted the solution as given here: 

[http://ubuntuforums.org/showthread.php?t=1583830&highlight=Keyring+password+disable&page=3](http://ubuntuforums.org/showthread.php?t=1583830&highlight=Keyring+password+disable&page=3)

I deleted the 'Passwords: default' under Passwords and Encryption Keys and made 'Passwords: login' the new default. Bad decision: It worked and on startup I was not asked for any keyring password however unfortunately I lost the ability to connect to the Internet. To be more precise the a pop-up appears saying that Wireless Network Authentication Required; but the Connect key is greyed-out. Similarly configuring the VPN also does not enable the Apply key. 

Is there some way for me to restore this and get the computer to work normally again. I believe I have deleted all stored passwords but am certain that the process can bf reversed.

Thanks and regards.

---

### Post by panderohit on 2011-04-29
Update: problem resolved. 

I resolved it as follows:

First, I choose Systems > Preferences > Passwords and Encryption Key > File> New...> Password Keyring > Continue > keyring name: default > Add

Then I right-clicked the new keyring in the list and 'Set it as Default'.

After this:
1. Right click the Netwprk Manager icon and select Edit Connections...
2. Select the wireless tab and select the network shown
3. Click on Edit followed by the Wireless Security tab. 
4. Entered the password and Apply

Hey, Presto! All resolved. And I'm back on but the keyring password is still asked for during log in. :(

I guess I'll have to live with it.

---

### Post by panderohit on 2011-07-26
Hi. I discovered that the best method to get around this is to disable start-up programmes. So I disabled the following from startup programmes: gwibber (deleted it, tweetdeck is better), ubuntu one, and skype. I also set it up to stop at the log-in screen instead of going straight through because I was getting some bugs when going straight through. So effectively I am entering the password only once (during log-in) but not thereafter, unless I need to use the said applications. But so far so good and not too irritating now.

---

