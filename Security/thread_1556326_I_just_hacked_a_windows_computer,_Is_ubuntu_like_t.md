---
title: "I just hacked a windows computer, Is ubuntu like that?!"
date: 2010-08-19
forum: Security
---

### Post by Ve5ahchoo8ah on 2010-08-19
I just checked something with my friend. He just gave me his IP and admin password and I could connect to his WindowsXP computer easily (just with some help about settings) and browse his computer!
We are both so scared that how easily it was to enter a computer!!

Is ubuntu like this?! I mean if someone find my root pass and my IP can he browse my computer as XP?
how about my user password? I'm the only user and administer (I can't change it to desktop user, it says because you are the only admin you can't)

another thing I want to ask is that there is lots of groups in my "user and group" isn't that something insecure? (because I remembered that in windows there was a way to use something like that)

---

### Post by endotherm on 2010-08-19
no. ubuntu ships with no network services installed or network ports open, so there is nothing to connect to, unless you open it up by installing server applications. 

your friend should disable remote desktop and Microsoft File and Print shareing if he/she is directly connected to the internet, or better yet, get a firewalling router. 

just be careful to not enable remote desktop or samba shared folders, and you will likely be fine.

the usergroup thing is not really an issue. I understand your concern, but your suspicion is purely anecdotal. the reason there are so many users/groups, is because each is very specifically preconfigured to have exactly the level of access it requires to perform a given task. most of these accounts will not support a login, so they are only for specific services. if you want to keep your user accounts secure, my best advice is don;t alter the standard settings for sudo/gksu (it prompts you for your password when doing something as admin) other than perhaps to make it forget the sudo password immediatly with each use, and do NOT enable the root account.

---

### Post by CharlesA on 2010-08-19
Linux is not Windows. As long as you don't enable "Remote Desktop" and secure services properly, you should be fine. Also, don't enable the root account, just use sudo to do admin stuff like updates and whatnot.

Also note: In the latest versions of Windows (Vista, 7), the administrator account is locked/disabled by default, so you cannot connect that way unless you know a set of valid credentials.

---

### Post by Ve5ahchoo8ah on 2010-08-19
thanks all
I know that on my friend's computer, remote desktop was off and File and Print shareing was on. (I thing it's the default!)
and CharlesA, could please say what do you mean by "secure services properly"?
I don't run any server on my computer. just surf the web with firefox , chat with pidgin, download with fatrat and transmission.
thanks you all

---

### Post by CharlesA on 2010-08-19
Services such as SSH or apache/whatever need to be secured properly, else yer box could become compromised. If you don't have those installed, then you are fine.

Also use apparmor and check out the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by rollin on 2010-08-19
> **CharlesA said:**
> 
Also note: In the latest versions of Windows (Vista, 7), the administrator account is locked/disabled by default, so you cannot connect that way unless you know a set of valid credentials.

You sure? Windows usually is an admin account by default. The UAC just requires password authentication of the admin account. It's not System32 but almost the equivalent of being root and still having sudo. Once this default and vulnerable account is accessed the ridiculous idea of a "hidden" admin account is too easily activated with the command:
net user administrator /active:yes

Linux is not similar to Windows in this regard at all. Sudo is far more secure than UAC. If your running Windows you should test the command above and set a very strong password for it. Then switch your everyday account to normal user and use the password to install / make changes to the system.

---

### Post by endotherm on 2010-08-19
> **rollin said:**
> You sure? Windows usually is an admin account by default. The UAC just requires password authentication of the admin account. It's not System32 but almost the equivalent of being root and still having sudo. Once this default and vulnerable account is accessed the ridiculous idea of a "hidden" admin account is too easily activated with the command:
net user administrator /active:yes

Linux is not similar to Windows in this regard at all. Sudo is far more secure than UAC. If your running Windows you should test the command above and set a very strong password for it. Then switch your everyday account to normal user and use the password to install / make changes to the system.
all true, save that the account you use by default (the first one created during setup) is not named 'Administrator'. the account localhost\administrator is locked and disabled by default on vista+. this is actually kinda helpful beyond the protection it gives you against account guessing attacks, because since the account is not in use, if you have to use a tool like the Offline NT Password and Registry Editor to unlock the account and blank it's password in an emergency, you can do so safely, as the account doesn't own any resources. just be sure to disable it again when you are done.

---

### Post by CharlesA on 2010-08-19
> **rollin said:**
> You sure? Windows usually is an admin account by default. The UAC just requires password authentication of the admin account. It's not System32 but almost the equivalent of being root and still having sudo. Once this default and vulnerable account is accessed the ridiculous idea of a "hidden" admin account is too easily activated with the command:
net user administrator /active:yes

If a clean install, it is disabled by default: [http://blogs.msdn.com/b/windowsvistasecurity/archive/2006/08/27/windowsvistasecurity_.aspx](http://blogs.msdn.com/b/windowsvistasecurity/archive/2006/08/27/windowsvistasecurity_.aspx)

> Linux is not similar to Windows in this regard at all. Sudo is far more secure than UAC. If your running Windows you should test the command above and set a very strong password for it. Then switch your everyday account to normal user and use the password to install / make changes to the system.

The above command will activate the (disabled) administrator account. It's not a problem if it's disabled. You can enable it, but you would need an administrative command prompt to do so.

---

### Post by rollin on 2010-08-19
> **endotherm said:**
> all true, save that the account you use by default (the first one created during setup) is not named 'Administrator'. the account localhost\administrator is locked and disabled by default on vista+.

Agreed but the default account is still capable of administrative functions. My advice to OP was just to enable the hidden admin account, the main target and set a strong password. Then set the everyday account as normal (I can't remember the exact term) and use the password to perform the admin functions. 

The fact that the admin account is locked by default means nothing if the default user (who has admin rights) is comprimised. It is literally as easy as the command I posted to enable it.

---

### Post by CharlesA on 2010-08-19
> **rollin said:**
> Agreed but the default account is still capable of administrative functions. My advice to OP was just to enable the hidden admin account, the main target and set a strong password. Then set the everyday account as normal (I can't remember the exact term) and use the password to perform the admin functions. 

The fact that the admin account is locked by default means nothing if the default user (who has admin rights) is comprimised. It is literally as easy as the command I posted to enable it.
That command needs a elevated command prompt, which you get prompted by UAC to allow or not.

I use a normal user with a seperate account (not administrator) for admin tasks.

---

### Post by rollin on 2010-08-19
> **CharlesA said:**
> That command needs a elevated command prompt, which you get prompted by UAC to allow or not.

I use a normal user with a seperate account (not administrator) for admin tasks.

OK. Perhaps I am not explaining my objective to OP so well. I am saying to enable the hidden admin account (which is a target on Windows systems) set a password and change all the other users to normal (or whatever the Win term is). The idea is to stop any programs from installing on the account without the user specifically choosing to use the Admin account password to verify the installation. 

I suppose my point is that running an account, which lets us say is comprimised, that has UAC is not as secure in any way to an account which requires another user to authenticate the installation of software. 

If the default user account has admin rights and the user account password is the only one controlling UAC and is comprimised then the whole system is also comprimised. 
Working as a normal user means that even if the account is comprimised with the password then the admin account and password still has to autheticate actions via UAC. Therefore the attacker has to gain rights not only to the everyday account but also has to somehow elevate the actions to the admin account to make changes to the system.

---

### Post by pricetech on 2010-08-19
The discussion is getting a little convoluted here.  I might make it even worse, but here goes anyway.

When you first use windows out of the box, you are prompted to enter a name.  This name becomes your username and has administrative access to the computer.  Therefore, this account can be used to compromise the system, with or without activating the default administrator's account.

Turning off file and printer sharing won't keep you from accessing the computer over the network either.  Windows creates certain shares by default.  They're hidden, but they're there.  If you have administrative credentials, you can access them.  It takes a registry hack to turn those off, though I've read it can be done in group policy, I just haven't tried it that way.

Nonetheless, your Linux box doesn't suffer from these security holes and as long as you don't set up some kind of remote access, remote login, etc. you have nothing to worry about.

---

### Post by BigCityCat on 2010-08-19
> **rollin said:**
> You sure? Windows usually is an admin account by default. The UAC just requires password authentication of the admin account. It's not System32 but almost the equivalent of being root and still having sudo. Once this default and vulnerable account is accessed the ridiculous idea of a "hidden" admin account is too easily activated with the command:
net user administrator /active:yes

Linux is not similar to Windows in this regard at all. Sudo is far more secure than UAC. If your running Windows you should test the command above and set a very strong password for it. Then switch your everyday account to normal user and use the password to install / make changes to the system.

I have Windows Seven set up as a standard user and I have an admin account. I tried your command with my standard user and got an access denied. So I am assuming that if you set up your accounts correctly from the beginning and you don't run as admin that this command has no effect.

---

### Post by BigCityCat on 2010-08-19
I think just to make it easy. It is advisable if your using windows to create a standard user account and an admin account. Set a very strong password for your admin account and only use you standard user regularly. This is how I operate when I am brave enough to use windows.

---

### Post by Camilia on 2010-08-19
> **CharlesA said:**
> don't enable the root account, just use sudo to do admin stuff like updates and whatnot.


Does this mean that is not wise to do updates via the synapse?

---

### Post by rollin on 2010-08-19
> **BigCityCat said:**
> I have Windows Seven set up as a standard user and I have an admin account. I tried your command with my standard user and got an access denied. So I am assuming that if you set up your accounts correctly from the beginning and you don't run as admin that this command has no effect.

I think if your using a standard account with a shortcut for cmd you would have to right click it and chooose run as administrator. 

> **BigCityCat said:**
> I think just to make it easy. It is advisable if your using windows to create a standard user account and an admin account. Set a very strong password for your admin account and only use you standard user regularly. This is how I operate when I am brave enough to use windows.

I completely agree! Have an everyday account and have an admin account to make changes. Whether people are going to take my advice and add password for the secret administrator account or create another user is kind of entirely up to them really. I'm not trying to make a policy for anyone here, the OP asked about Windows so I mentioned it. People can make their own minds up how they want to run their system without my advice LOL. ;)

---

### Post by CharlesA on 2010-08-19
> **Camilia said:**
> Does this mean that is not wise to do updates via the synapse?

That's the same thing.

---

### Post by linux18 on 2010-08-19
> **CharlesA said:**
> 
The above command will activate the (disabled) administrator account. It's not a problem if it's disabled. You can enable it, but you would need an administrative command prompt to do so.
However, you can get into an administrator account through a 'safety' measure in the login screen.

---

### Post by CharlesA on 2010-08-19
> **linux18 said:**
> However, you can get into an administrator account through a 'safety' measure in the login screen.

When it's disabled? It's not possible to login on a disabled account.

You need to start an administrative command prompt to enable it, which triggers UAC, and if don't bother reading what the prompt says, you need to slow down and stop being click happy.

That's a general "you" by the way. :)

---

### Post by JustChris21 on 2010-08-19
> **samic130 said:**
> I just checked something with my friend. He just gave me his IP and admin password and I could connect to his WindowsXP computer easily (just with some help about settings) and browse his computer!
We are both so scared that how easily it was to enter a computer!!

Is ubuntu like this?! I mean if someone find my root pass and my IP can he browse my computer as XP?
how about my user password? I'm the only user and administer (I can't change it to desktop user, it says because you are the only admin you can't)

another thing I want to ask is that there is lots of groups in my "user and group" isn't that something insecure? (because I remembered that in windows there was a way to use something like that)

Out of curiosity, what protocol did you use to connect to his IP? i.e. on a linux computer you could use SSH if the host computer had it enabled.

---

### Post by rollin on 2010-08-19
> **CharlesA said:**
> When it's disabled? It's not possible to login on a disabled account.

You need to start an administrative command prompt to enable it, which  triggers UAC, and if don't bother reading what the prompt says, you need  to slow down and stop being click happy.

That's a general "you" by the way. :)

I think linux18 is talking about Utilman tool on Backtrack which requires physical  access see  [http://www.offensive-security.com/videos/owning-windows-vista-video/hacking-vista-with-backtrack.html](http://www.offensive-security.com/videos/owning-windows-vista-video/hacking-vista-with-backtrack.html)  for an example.

---

### Post by endotherm on 2010-08-19
> **Camilia said:**
> Does this mean that is not wise to do updates via the synapse?
no, thats not what it means. when you run synaptic, you are running as yourself, but using admin powers. we are discussing the caveats of enabling the root account itself, an logging in as root itself. which is bad...

---

### Post by CharlesA on 2010-08-19
> **rollin said:**
> I think linux18 is talking about Utilman tool on Backtrack which requires physical  access see  [http://www.offensive-security.com/videos/owning-windows-vista-video/hacking-vista-with-backtrack.html](http://www.offensive-security.com/videos/owning-windows-vista-video/hacking-vista-with-backtrack.html)  for an example.

I see. I guess it still deals with the whole "physical access = root access" thing. ;)

---

### Post by rollin on 2010-08-19
> **CharlesA said:**
> I see. I guess it still deals with the whole "physical access = root access" thing. ;)

I think you're right ;) Not exactly the most subtle of exploits LOL.

---

### Post by linux18 on 2010-08-19
if you have physical access you can always get root access, no matter which computer it is or at the very least, format their hard disk. the computers at the college I go to were running NT4 (cool) then upgraded to xp (ok) then upgraded to win 7 (noooooooo!) I need puppy linux just to get them to start sometime today and I would dual boot linux on those computers if I wasn't going to get caught (no matter what happens, it's my fault, has been the campus police's computer policy.... unfortunately they are right)

---

