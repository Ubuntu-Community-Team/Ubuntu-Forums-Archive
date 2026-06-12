---
title: "Set/reset any root or user password."
date: 2016-08-25
forum: Security
---

### Post by T2uiYKb7 on 2016-08-25
I remember being dumbfounded 8 years ago when I realized Linux ignored NTFS permissions. I remember saying 

"What do you mean "ignores"? That's impossible. That means I can access any unencrypted file on any Windows machine I have physical access to, how could they let that happen?"

I haven't come across anything like that on Linux until 5 minutes ago. Two tiny commands from any Live CD and people can set/reset any root or user password. What in the world? I could lock people out of there own systems (change password then add BIOS password), read personal and private messages (actually login into there account, not just read files, use there Firefox with all there logins etc.) , steal intellectual property the possibilities are endless. On any Linux PC that doesn't disable USB boot *and* lock there BIOS.

Why does Linux allow this? 

This is madness!

---

### Post by QIII on 2016-08-25
You have only now realized that physical access is root access?

And please do not reverse Staff edits.

---

### Post by T2uiYKb7 on 2016-08-25
I PM'd you and apologized , I thought my browser my mucking up I didn't realize you were removing my 300 picture.

I knew Live CD's gave root permissions to any file system, as in I can modify any unencrypted file. I just expected there was encryption or some safeguard around reseting [B]*other people's passwords, passwords on totally different OS's.*

[/B]This isn't a personal attack, I love Linux and I'm sure no one here has made this decision.

---

### Post by &amp;KyT$0P# on 2016-08-25
On the plus side, you can do those things to **your own OS** if you have a OS disaster and need recovery.  It happens, I've had to do it before.

> **andrew.nz said:**
> I just expected there was encryption or some safeguard around reseting ***other people's passwords, passwords on totally different OS's.***
If there is some such encryption or safeguard it's up to that other person and their OS to implement it and use it.

---

### Post by T2uiYKb7 on 2016-08-25
Wow everything is getting edited. Is this a taboo subject?

Why hasn't Linux set up some sort of encryption of the file that stores password? One that is only decrypted on boot of that particular OS?

That would mean an external root that changed the file to an unencrypted human readable format wouldn't be able to have full control of any user on that PC.

Are Linux passwords stored in a human readable format?

---

### Post by QIII on 2016-08-25
Physical access is root access.  This fact of life was known to me in the 70s.  There is no surprise here.

What you have learned is one of the basic tenets of computer security.  Investigate further and build on this.

---

### Post by QIII on 2016-08-25
> **andrew.nz said:**
> Wow everything is getting edited. Is this a taboo subject?

No.  Just keeping the discussion on track.

> Why hasn't Linux set up some sort of encryption of the file that stores password? One that is only decrypted on boot of that particular OS?

There are apps that do that.  There are files already that encrypt passwords and such.

> That would mean an external root that changed the file to an unencrypted human readable format wouldn't be able to have full control of any user on that PC.  

Physical access is root access.  That means this extra external root can be compromised.

> Are Linux passwords stored in a human readable format?

Generally not if you set things up for them not to be.  But some are, depending on the application.

---

### Post by T2uiYKb7 on 2016-08-25
Please don't be-little me. No need to be condescending. 

There are methods of encryption that would make it much harder for a user to do this.

---

### Post by lisati on 2016-08-25
This is not a taboo subject. The basic premise is that "Physical access = root access." Having said that, there are tools and techniques you can apply to help reduce the risk of unwanted access.

---

### Post by 1clue on 2016-08-25
Physical access to any machine with unencrypted partitions means that data is readable to whoever has access. Put the windows drive in a Linux box and you have access to any files on it. Pretty much anything.

Even with a bios password you can reset the motherboard and get in

---

### Post by QIII on 2016-08-25
Or move the drive to another machine.

> Please don't be-little me. No need to be condescending.

I am not being condescending.  I am informing you.  You have found something that is novel to you, but I assure you that it is not novel to all of us.

People have been mulling these issues for decades.  You may very well be the one who develops the silver bullet we have all been waiting for.  Until you do, we use security procedures and processes to mitigate risks.

---

### Post by &amp;KyT$0P# on 2016-08-25
> **andrew.nz said:**
> Are Linux passwords stored in a human readable format?
See for yourself in the shadow files in /etc, do you call that human-readable?

> **andrew.nz said:**
> There are methods of encryption that would make this much harder for a user to do this.
So use them if you think it's useful to you.  Evidently, the owner of the computer in question don't think so.
Different people have different needs and standards, one size computer security doesn't exist.

---

### Post by T2uiYKb7 on 2016-08-25
The fact that applications can harden this or make it impossible means that outside roots don't always have absolute control.

Encryption is key I'm guessing. Why don't they implement this by default?

Ps: I understand NTFS security is useless when looking at it with Linux.

---

### Post by T2uiYKb7 on 2016-08-25
> **1clue said:**
> Physical access to any machine with unencrypted partitions means that data is readable to whoever has access. Put the windows drive in a Linux box and you have access to any files on it. Pretty much anything.

Even with a bios password you can reset the motherboard and get in

I've always known that, what surprises me is reseting root/user passwords, ie. there not encrypted etc.

> **QIII said:**
> Or move the drive to another machine.



I am not being condescending.  I am informing you.  You have found  something that is novel to you, but I assure you that it is not novel to  all of us.

People have been mulling these issues for decades.  You may very well be  the one who develops the silver bullet we have all been waiting for.   Until you do, we use security procedures and processes to mitigate  risks.


The fact root on a Live CD (or the OS mounting another OS) has absolute control over unencrypted files is **not** new to me. 

Your still being condescending and defensive bro.

**This is my point:**

Logging in as someone opens up a whole bunch of possibilities (on line logins, identity theft, extortion) that viewing there files outside there OS doesn't.

**Edit: It also make encrypting your home folder pointless (just login as them.)**

---

### Post by 1clue on 2016-08-25
> **andrew.nz said:**
> 
Why hasn't Linux set up some sort of encryption of the file that stores password? One that is only decrypted on boot of that particular OS?

That would mean an external root that changed the file to an unencrypted human readable format wouldn't be able to have full control of any user on that PC.

Are Linux passwords stored in a human readable format?

Pardon errors, typing from my phone. 

Linux uses a 1-way hash for passwords. That allows from an administrator to boot from a rescue cd and reset passwords if the file is corrupted or the root user gets hit by a bus.

There's really no security that can protect a computer from physical access. If the computer can boot without humans providing an encryption key then some third party who can get the box can get what's on it.

An exception is any data that's encrypted, for example your home directory, if the user provides the key.

This is why server rooms have locks on the doors.

---

### Post by lisati on 2016-08-25
There's a sure fire way of preventing unwanted access: disconnect the computer completely from the outside world, dismantle it, and bury it in concrete. Because this can effectively render the machine totally useless for the typical user, we tend to use other tools, of which strong encryption is one option.

---

### Post by T2uiYKb7 on 2016-08-25
> **1clue said:**
> Pardon errors, typing from my phone. 

Linux uses a 1-way hash for passwords. That allows from an administrator to boot from a rescue cd and reset passwords if the file is corrupted or the root user gets hit by a bus.

There's really no security that can protect a computer from physical access. If the computer can boot without humans providing an encryption key then some third party who can get the box can get what's on it.

An exception is any data that's encrypted, for example your home directory, if the user provides the key.

This is why server rooms have locks on the doors.

Couldn't I just change that users password (from my Live CD), login as them and view/copy all there now unencrypted data?

---

### Post by T2uiYKb7 on 2016-08-25
> **lisati said:**
> There's a sure fire way of preventing unwanted access: disconnect the computer completely from the outside world, dismantle it, and bury it in concrete. Because this can effectively render the machine totally useless for the typical user, we tend to use other tools, of which strong encryption is one option.

I'm not paranoid when it comes to security. I've never used anti-virus on Linux and it's not a reason I moved away from Windows.

But doesn't this also make encrypting data in the home folder/partition 99% pointless. Simply reset there password and login as them.

---

### Post by &amp;KyT$0P# on 2016-08-25
> **andrew.nz said:**
> I've always known that, what surprises me is reseting root/user passwords, ie. there not encrypted etc.


The fact root on a Live CD (or the OS mounting another OS) has absolute control over unencrypted files is **not** new to me. 
You can't have it both ways, either this is or isn't news to you.

> Logging in as someone opens up a whole bunch of possibilities (on line logins, identity theft, extortion) that viewing there files outside there OS doesn't.
You do realize someone's local user account is basically nothing other than their files right?

User don't log in to online accounts with their local user account.  If the bad guy with physical access to the machine is going to do evil with online logins, they can just copy the browser profile or whatever and use/extract credentials from there on their own machine, no need even touching the victim's local login.

---

### Post by &amp;KyT$0P# on 2016-08-25
> **andrew.nz said:**
> Couldn't I just change that users password (from my Live CD), login as them and view/copy all there now unencrypted data?
How does changing a password decrypt anything?  Nowhere in that process do you have the old password (nor encryption password, if different).

---

### Post by T2uiYKb7 on 2016-08-26
> **halogen2 said:**
> You can't have it both ways, either this is or isn't news to you.


You do realize someone's local user account is basically nothing other than their files right?

User don't log in to online accounts with their local user account.  If the bad guy with physical access to the machine is going to do evil with online logins, they can just copy the browser profile or whatever and use/extract credentials from there on their own machine, no need even touching the victim's local login.

Dude the fact there's no safeguards or encryption around passwords is whats new to me.

The fact it makes encrypting your home folder pointless.

I know the home folder is not system files, I'm not talking about breaking there OS I'm talking about stealing information, seeing private files, logging into email accounts etc.

---

### Post by T2uiYKb7 on 2016-08-26
> **halogen2 said:**
> How does changing a password decrypt anything?  Nowhere in that process do you have the old password (nor encryption password, if different).

Change there password. Reboot PC (take out Live CD) login as user. View all private files, login to email, Facebook.

---

### Post by QIII on 2016-08-26
I'm not sure what makes you think encrypting your /home is pointless.

---

### Post by lisati on 2016-08-26
> **andrew.nz said:**
> The fact it makes encrypting your home folder pointless.
Without the proper passphrase, which can be different to the password used to login, it can be very difficult to recover the person's data.

---

### Post by T2uiYKb7 on 2016-08-26
Ok I'm asking this (not ranting :).) If I changed the root password then rebooted back into the OS. Changed the password for ***johnadmin*** to ***gotyaprivatestuff*** then logged in as ***johnadmin*** would I not have access to his private stuff?

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Ok I'm asking this (not ranting :).) If I changed the root password then went rebooted back into the OS. Change the password for ***johnadmin*** to ***gotyaprivatestuff*** then logged in as ***johnadmin*** would I not have access to his private stuff?

If johnadmin had an encrypted home directory then no you would not have access to his private stuff.

---

### Post by 1clue on 2016-08-26
The encryption key is typically something which is not stored on the computer. It's unreachable unless the user is logged in.  It can be a memorized passphrase, or a usb stick with an encryption key on it, or something else.

---

### Post by 1clue on 2016-08-26
You can also encrypt the entire hard disk by using an external key. At any rate the only way you would have the data is if:
[LIST=1]
[*]you broke the encryption
[*]the guy left his key on the system
[*]the guy wrote the key on a piece of paper and left it under the keyboard.  Or some equally inane place.
[*]the guy did something incredibly stupid like saving the key on the hard drive
[/LIST]

---

### Post by T2uiYKb7 on 2016-08-26
Like I said I'm not an overly security conscious guy I've used Linux for 8 years and never encrypted my /home. I'm guessing any business user does, anyone with relatively private/valuable information. 

Question: So that encryption key is separate and is entered in **addition** to the login password? And that encryption key **can't **be reset by a root thats mounted that OS?

If that is the case:

A.) Awesome :)

B.) Why on earth don't they use the same system for login passwords?

---

### Post by QIII on 2016-08-26
There seems to be a misapprehension here that having the login password is the same as having the encryption key.  This is not necessarily the case.  Nor does that guarantee that it is the same as having the pass-phrase to a keyring.

---

### Post by 1clue on 2016-08-26
All that said, if you are logged in with an encrypted home directory and some malware is running, then your data is available anyway.  On any operating system, not just Linux. Especially when you consider that most attacks involve convincing a user to do something stupid.

There is absolutely no fail-safe way to protect your data.  Except to disconnect it from the world, which was mentioned before.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> The encryption key is typically something which is not stored on the computer. It's unreachable unless the user is logged in.  It can be a memorized passphrase, or a usb stick with an encryption key on it, or something else.

So all the user has to do is login? And that can be reset by any Live CD?

So I am right?

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Like I said I'm not an overly security conscious guy I've used Linux for 8 years and never encrypted my /home. I'm guessing any business user does, anyone with relatively private/valuable information. 

Question: So that encryption key is separate and is entered in **addition** to the login password? And that encryption key **can't **be reset by a root thats mounted that OS?

If that is the case:

A.) Awesome :)

B.) Why on earth don't they use the same system for login passwords?

A.) Maybe.

B.) Because for most uses it's a pain in the rear and not nearly worth the effort.

I've been using Linux for 20 years. Back then the passwords were plain text on the distros I used. Shortly after they changed it to be a bit more difficult.

The current system of a 1-way hash is there for a reason. Most Linux boxes which are being used by businesses have multiple admins, and lost data means lost money. If you have everything encrypted and the guy who knows the password gets hit by a bus, or is fired, then not being able to get the data is really bad for the owner of the system.  Who is almost certainly not the administrator.

Let's revisit:  If you have everything encrypted then forgetting your encryption password, or losing your key at the bottom of the lake you were fishing at, means you just threw away all your data.  Using the 1-way hash, you can reset your password with the live cd and be back in business in 5 minutes.

---

### Post by T2uiYKb7 on 2016-08-26
> **QIII said:**
> There seems to be a misapprehension here that  having the login password is the same as having the encryption key.   This is not necessarily the case.  Nor does that guarantee that it is  the same as having the pass-phrase to a keyring.

Can I have a straight answer here? If I have someones password I can  login as them and see there files right? As in boot into the install of  there OS and view there files even if there home is encrypted?

If that is the case encrypting home **is** pointless because I can simply change there password, reboot log into **there **OS and see everything.

The whole point of encryption is to protect against physical in person attacks. Eg. encrypting your Android phone, they can steal it, wipe it and use it. But they can't see the photos of you  and ya mate's girlfriend. Or private business reports.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> 
Let's revisit:  If you have everything encrypted then forgetting your encryption password, or losing your key at the bottom of the lake you were fishing at, means you just threw away all your data.  Using the 1-way hash, you can reset your password with the live cd and be back in business in 5 minutes.

Thank you, so encrypting /home is 99.9% pointless.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Can I have a straight answer here? If I have someones password I can  login as them and see there files right? As in boot into the install of  there OS and view there files even if there home is encrypted?

If that is the case encrypting home **is** pointless because I can simply change there password, reboot log into **there **OS and see everything.

The whole point of encryption is to protect against physical in person attacks. Eg. encrypting your Android phone, they can steal it, wipe it and use it. But they can't see the photos of you  and ya mate's girlfriend.

Come on.

The only way that having someone's password gets you access to their encrypted data is if the login password is the same as the encryption password.  In that case, changing their password causes the data to be irretrievably lost, because you didn't have the old password to decrypt it with. So by logging in from a live cd and changing their password, you've essentially turned the user's home directory into random noise which cannot be retrieved.

There are dozens or hundreds or thousands of ways to implement encryption on a computer.  Go read some encryption howto's and they'll probably mention 3 or 4 ways. You as the engineer of this system need to evaluate your scenario and balance security with convenience.

---

### Post by 1clue on 2016-08-26
As I and several others have been saying all along, there's a login password which is in /etc/secret (encrypted with a 1-way hash), and then there's an encryption key which must be added to the system before the encrypted data is available.

[COLOR=#ff0000][SIZE=5]They are NOT the same thing.[/SIZE][/COLOR]

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> Come on.

The only way that having someone's password gets you access to their encrypted data is if the login password is the same as the encryption password.  In that case, changing their password causes the data to be irretrievably lost, because you didn't have the old password to decrypt it with. So by logging in from a live cd and changing their password, you've essentially turned the user's home directory into random noise which cannot be retrieved.

There are dozens or hundreds or thousands of ways to implement encryption on a computer.  Go read some encryption howto's and they'll probably mention 3 or 4 ways. You as the engineer of this system need to evaluate your scenario and balance security with convenience.

What if I create a root password. Open a virtual terminal login as root and change the user password within **there** OS?

(Question not rant.)

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Thank you, so encrypting /home is 99.9% pointless.

Are you even reading what we're saying?

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> What if I create a root password. Open a virtual terminal login as root and change the user password within **there** OS?

(Question not rant.)

1. It's **their** OS.
2. You don't have their encryption key, so you don't have their data.

---

### Post by 1clue on 2016-08-26
Let me start again.

If the encryption scheme was intelligently handled, then as long as you do not have their encryption key (NOT THE LOGIN PASSWORD) then you do NOT have their data. Or you could crack it, if you have access to a cloud of supercomputers to crack the encryption.

Do you remember the apple iphone incident?

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> As I and several others have been saying all along, there's a login password which is in /etc/secret (encrypted with a 1-way hash), and then there's an encryption key which must be added to the system before the encrypted data is available.

[COLOR=#ff0000][SIZE=5]They are NOT the same thing.[/SIZE][/COLOR]

Peace cuz. I'll do a VirtualBox install and muck around and get back to you.

Regardless it lets you log into the email accounts, Facebook, FTP servers, LinkedIn, stock exchange accounts etc. on any unencrypted user. (Eg. log into there account rather than view files.) 

So I stand by my *"This is madness" *statement."

---

### Post by 1clue on 2016-08-26
The login password is encrypted with a 1-way hash and stored in /etc/shadow. It is used to login to the system, and this is what you change when you use root account or a live cd to change passwords.

The encryption key is (should be) never attached to the computer unless the user is logged in. If the user didn't forget the key in the USB slot then you don't have his data.

---

### Post by lisati on 2016-08-26
I can only repeat what others have said: changing a user's login password will not give you access to their data if it's encrypted. You will need an appropriate passphrase to decode the data.

To put it another way, encrypting your data is intended to protect it from being used by others without your permission, and not to prevent you from using it.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> 1. It's **their** OS.
2. You don't have their encryption key, so you don't have their data.

But I have **their** root password. Their OS doesn't know I reset it externally right?

---

### Post by T2uiYKb7 on 2016-08-26
> **lisati said:**
> To put it another way, encrypting your data is intended to protect it from being used by others without your permission, and not to prevent you from using it.

I understand that (hence my Android example.)

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Peace cuz. I'll do a VirtualBox install and muck around and get back to you.

Regardless it lets you log into the email accounts, Facebook, FTP servers, LinkedIn, stock exchange accounts etc. on any unencrypted user. (Eg. log into there account rather than view files.) 

So I stand by my *"This is madness" *statement."

If their user account is encrypted and you changed the password using root or a live cd, then you DO NOT HAVE ACCESS. All that data is encrypted in the /home/user directory, and you don't have the key.

---

### Post by QIII on 2016-08-26
> **andrew.nz said:**
> Regardless it lets you log into the email accounts, Facebook, FTP servers, LinkedIn, stock exchange accounts etc. on any unencrypted user. (Eg. log into there account rather than view files.)

Also:

Not if none of the passwords/phrases/keys are stored on the machine.
Not if the passwords/phrases/keys are stored in a keyring or something like KeyPass that is itself encrypted.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> If their user account is encrypted and you changed the password using root or a live cd, then you DO NOT HAVE ACCESS. All that data is encrypted in the /home/user directory, and you don't have the key.

I used the word unencrypted.

---

### Post by 1clue on 2016-08-26
If you change the password using root or live cd, then login as that user, your home directory is random noise and you will get errors, and probably be unable to login at all.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> I used the word unencrypted.

Yes you did, my apologies.  That said, I can change a Windows or Mac user password as well and get the same exact access.

---

### Post by T2uiYKb7 on 2016-08-26
> **QIII said:**
> Also:

Not if none of the passwords/phrases/keys are stored on the machine.
Not if the passwords/phrases/keys are stored in a keyring or something like KeyPass that is itself encrypted.

I was saying *un*encrypted in that example. I did that today so I know that's how it works for unencrypted home folders.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> Yes you did, my apologies.  That said, I can change a Windows or Mac user password as well and get the same exact access.

I guess I was used to my false sense of security.

---

### Post by QIII on 2016-08-26
If it's unencrypted, then physical access = root access.

I have preached against the Linux brand of false sense of security for years.

---

### Post by 1clue on 2016-08-26
Almost all security is a false sense of security.  Not even the Pentagon can keep everyone out of their business.

I know of no arrangement where a logged-in user who opens malware (inadvertently or not) is protected whether the home directory is encrypted or not.  If the malware is running under the logged-in user's account, then the data is effectively not encrypted, because the encryption layer is transparent after the key is enabled.

This is true for any operating system.

---

### Post by T2uiYKb7 on 2016-08-26
> **QIII said:**
> If it's unencrypted, then physical access = root access.

Were taking in ***circles*** now bro, we've established simply encrypting the individual file that store passwords would avoid that.

I'm talking **logging into accounts **not viewing/deleting/modifying files. 

My Lastpass (browser passwords) account (Facebook, Emails, Stocks) is encrypted to **everyone** unless I'm** logged into** my Linux user. Then there's also the case of locking people out of there system.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> Almost all security is a false sense of security.  Not even the Pentagon can keep everyone out of their business.

I know of no arrangement where a logged-in user who opens malware (inadvertently or not) is protected whether the home directory is encrypted or not.  If the malware is running under the logged-in user's account, then the data is effectively not encrypted, because the encryption layer is transparent after the key is enabled.

This is true for any operating system.

Encrypting files within the users account (ie TrueCrypt etc.) can help with that. And not giving them administrator/sudo rights protects the system.

I know nothing is perfect I just think making hard is a start.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Were taking in ***circles*** now bro, we've established simply encrypted the individual file that store passwords would avoid that.


No. If root user (not a live cd) changes your password, then simply encrypting the file that stores passwords will not protect you in that case.  The passwords are already encrypted.

> 
I'm, talking **logging into accounts **not viewing/deleting/modifying files. 

My Lastpass (browser passwords) account (Facebook,Emails, Stocks) is encrypted **everyone** unless I'm** logged into** my Linux user. Then there's also the case of locking people out of there system.

If the data is not directly encrypted, then it's not encrypted.  Anyone can get it, whether logged into the real operating system on the computer with admin access or by taking the drive out and putting it on another computer, or using a live cd.

If your password saver does not require a password every time you use it, then it's not a sure protection.

---

### Post by 1clue on 2016-08-26
Come to think of it, if you're using a web browser for stocks and emails then your password saver is probably not being used.  It's going to be your web browser settings/cache files.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> If the data is not directly encrypted, then it's not encrypted.  Anyone can get it, whether logged into the real operating system on the computer with admin access or by taking the drive out and putting it on another computer, or using a live cd.

If your password saver does not require a password every time you use it, then it's not a sure protection.

Your over simplifying there are ways software can tell what OS there running on many do it. **All** paid software that requires a license does it, with and without the internet.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> Come to think of it, if you're using a web browser for stocks and emails then your password saver is probably not being used.  It's going to be your web browser settings/cache files.

There job is to patch those flaws, it's very complex and beyond my understanding (in terms of specifics.) You can't just copy and paste it.

---

### Post by 1clue on 2016-08-26
There goes your false sense of security again.  Quite a bit of paid software that I own only looks for a valid key file.

At any rate what I said is correct. If your data is not encrypted then it's not encrypted. If the data is stored on your hard drive, not encrypted, then it's available to anyone who can make sense of it.

---

### Post by T2uiYKb7 on 2016-08-26
> **1clue said:**
> There goes your false sense of security again.  Quite a bit of paid software that I own only looks for a valid key file.

At any rate what I said is correct. If your data is not encrypted then it's not encrypted. If the data is stored on your hard drive, not encrypted, then it's available to anyone who can make sense of it.

Dude come on. Because someone eventually got around the defenses of certain paid software does not make you 100% right and me 100% wrong.

Let's be mature.

---

### Post by T2uiYKb7 on 2016-08-26
I'll catch you guys up later I've been sitting here too long.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> There job is to patch those flaws, it's very complex and beyond my understanding (in terms of specifics.) You can't just copy and paste it.

Yes, you can copy/paste web browser passwords.  I've done it just to satisfy my own curiosity. And it was a bank password.

There are mechanisms you can use to prevent it, but that does not mean every website does so.

The reason we're still going around like this is because you're making obvious assumptions that are not always true. It's better to not make blanket statements and accept that security is not perfect. A level of distrust is healthy when it comes to your private data.

---

### Post by lisati on 2016-08-26
> **andrew.nz said:**
> I'll catch you guys up later I've been sitting here too long.

We all need a break from time to time. I think a rerun of the Simpsons is on in the place of Home and Away tonight. Mrs Lisati will probably watch the 5:30 news on another station instead.

---

### Post by T2uiYKb7 on 2016-08-26
With the latest versions of Firefox you cannot copy and paste the entire cache/profile (from an external OS) and use there passwords. Not on any major website anyway. 

Catch ya'll later.

---

### Post by T2uiYKb7 on 2016-08-26
[COLOR=#006400]**Edit**[/COLOR][B][COLOR=#006400]: Not quite what I thought, perhaps too long in front of a screen today.

[/COLOR][/B][COLOR=#006400][/COLOR][COLOR=#000000]I still stand by my original statement that it's insane that the default Ubuntu install lets you access all accounts simply by reseting passwords with any Live CD. (Hijack email accounts etc.)[/COLOR][COLOR=#006400][/COLOR][B][COLOR=#006400]

[/COLOR][/B][COLOR=#000000]A lil pizaz gone out of that argument now tho lol[/COLOR]**[COLOR=#006400] :) [/COLOR]**

---

### Post by QIII on 2016-08-26
How did you encrypt the /home directory?

---

### Post by T2uiYKb7 on 2016-08-26
I encrypted as I was prompted. I ticked the "Encrypt home folder" then once I logged in I entered a huge jumbled password as the encryption key.

It definitely encrypted correctly because I couldn't access those home folders from the Live CD and the user login I reset **directly** from the Live CD (not via my new root user) didn't work once I rebooted.

---

### Post by QIII on 2016-08-26
And you could actually open and view files in an encrypted directory without a mount passphrase or anything like that?

This was the standard encryption available at installation, right?

I'm saying ***open*** the files, not see that they are there.

---

### Post by T2uiYKb7 on 2016-08-26
I logged into the users that had encrypted home folders and I could open and view the files correctly.

Only the users who's passwords I reset **after** I logged back in with my **new** root password.

---

### Post by QIII on 2016-08-26
So you did a password change as an administrator without providing the original password?

---

### Post by T2uiYKb7 on 2016-08-26
Yes on the Live CD , all successful encrypted user logins were done by changing there password while logged into the HDD install. With the root I reset (without knowing) on the Live CD.

---

### Post by QIII on 2016-08-26
So you have defeated PAM?

---

### Post by T2uiYKb7 on 2016-08-26
?

I'm guessing thats a coded insult.

I've shown encrypting home folders has zero effect on a malicious user who is physically in front of an Ubuntu install.

---

### Post by QIII on 2016-08-26
No, you haven't shown that.  You have told us what you *said* has happened.  Either you have misunderstood what you have done or something was set up improperly to begin with.

PAM (Pluggable Authentication Modules) will not allow the re-encryption of the /home/you directory passphrase in an administrative mode without providing the original password.  This is by design and it is to *prevent* exactly what you are saying you have done.  If you use the passwd command from the terminal to change your own password, your home directory passphrase is re-encrypted with your new password.

If done as an administrator, then the re-encryption can be done by issuing

```
ecryptfs-mount-private
``` with your *old password*, followed by ```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

If the simple process you are claiming were true, then you are too late in finding it.  Every Linux machine on Earth is already pwned.

---

### Post by T2uiYKb7 on 2016-08-26
I'm not mistaken.

I'm using Lubuntu 16.04 and this is what happened. Please try it in VirtualBox (won't take long) before calling me a liar.

---

### Post by T2uiYKb7 on 2016-08-26
Maybe it's a bug in Lubuntu , maybe it's a bug in any 16.04 Buntu , or just before a certain update but I'm not lying.

Maybe somehow it just happens in VirtualBox.

---

### Post by QIII on 2016-08-26
I needn't try it, thanks.

And I did not call you a liar.

If you think it may be a bug, you should report it.

---

### Post by T2uiYKb7 on 2016-08-26
What have you got to lose? 10 minutes?

---

### Post by QIII on 2016-08-26
If you think it's a bug, report it.

---

### Post by T2uiYKb7 on 2016-08-26
I just tried again and then with 15.10 and it didn't work. Guess I got a little ahead of myself.

---

### Post by T2uiYKb7 on 2016-08-26
I still by my original outrage of being able to cause mayhem, lock people out, hijack email accounts on systems **without** encrypted home drives. :)

---

### Post by QIII on 2016-08-26
You could not repeat the results of your experiment, but yet maintain it was correct?

---

### Post by T2uiYKb7 on 2016-08-26
No I guess that was my mistake somehow, in regards to such a simple way to get around encrypted /home folders. Perhaps just too long in front of a screen today.

I'm saying I stand by everything I said about **un**encrypted /home folders and that at least the file were all passwords are stored  should be encrypted in **every** install.

---

### Post by T2uiYKb7 on 2016-08-26
I'll take it on the chin that somehow I mixed my experiment up in regards to the **encrypted** /home folders.

---

### Post by sudodus on 2016-08-26
This discussion made me curious, so I installed a system, and made a second user with 'encrypted home'. That second user saved a file it its home directory.

I found what I may call a glitch. After logout and login to the first user, the saved file in the second user's home directory is still available from the first user (via sudo). But after shutdown or reboot, it is not available until the second user logs in. ***So if there are more than one user in the computer, you should shutdown or reboot to clear the memory to wipe your traces***.

I also changed the password of the second user. That made it impossible to access the encryption (like it should be). I could log in to the second user, but the encrypted file (in the home directory) was not available. It complained

'Signature not found in the user keyring. Perhaps try interactive 'ecryptfs-mount-private'.

(And that works only if you have saved the passphrase for the encryption.) I could not find (and not read) the file from a live system.

I changed back to the original password of the second user, and the encrypted file was available again, when logged in as the second user.

-o-

Another alternative is 'encrypted disk' alias 'LVM with encryption'. You get as one alternative at the partitioning windows during the installation. This is what I would recommend for a laptop computer, that you use during traveling. Maybe it will be easier for you to trust such a system. But no system is 100 % safe and possible to use at the same time.

---

### Post by QIII on 2016-08-26
The memory thing really is an interesting -- and potentially dangerous -- phenomenon.

---

### Post by T2uiYKb7 on 2016-08-26
> **sudodus said:**
> This discussion made me curious, so I installed a system, and made a second user with 'encrypted home'. That second user saved a file it its home directory.

I found what I may call a glitch. After logout and login to the first user, the saved file in the second user's home directory is still available from the first user (via sudo). But after shutdown or reboot, it is not available until the second user logs in. ***So if there are more than one user in the computer, you should shutdown or reboot to clear the memory to wipe your traces***.

I also changed the password of the second user. That made it impossible to access the encryption (like it should be). I could log in to the second user, but the encrypted file (in the home directory) was not available. It complained

'Signature not found in the user keyring. Perhaps try interactive 'ecryptfs-mount-private'.

(And that works only if you have saved the passphrase for the encryption.) I could not find (and not read) the file from a live system.

I changed back to the original password of the second user, and the encrypted file was available again, when logged in as the second user.

-o-

Another alternative is 'encrypted disk' alias 'LVM with encryption'. You get as one alternative at the partitioning windows during the installation. This is what I would recommend for a laptop computer, that you use during traveling. Maybe it will be easier for you to trust such a system. But no system is 100 % safe and possible to use at the same time.

I'm 80% (maybe 70%) certain I saw unencrypted files when I shouldn't have, at least once briefly, perhaps it was something along these lines. (Or perhaps I got my unencrypted user mixed up with my encrypted user.)

---

### Post by sudodus on 2016-08-26
I thought this 'memory effect' might explain your experience :-)

---

### Post by T2uiYKb7 on 2016-08-26
Only the Linux gods will ever truly know :)

I'll be more methodical next time I try something like that, screenshots and notes.

---

### Post by T2uiYKb7 on 2016-08-26
I feel silly in hindsight but it seemed silly to me how easy it was to change root and sudoers passwords too so it didn't seem so far off.

Slightly off topic but is there a performance drop if someone encrypts an entire installation? When you first install a Buntu from USB or DVD there's an option.

---

### Post by sudodus on 2016-08-26
I think so, but not much. I suggest that you test it, if you have a spare hard disk drive, SSD, or [fast USB 3 pendrive](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed).

---

### Post by 1clue on 2016-08-26
***Edit:** I responded to posts in order.  I left the posts in place, but understand that the tone of the thread has changed and I did not know that right away.*

> **andrew.nz said:**
> [COLOR=#006400]**Edit**[/COLOR][B][COLOR=#006400]: Not quite what I thought, perhaps too long in front of a screen today.

[/COLOR][/B][COLOR=#000000]I still stand by my original statement that it's insane that the default Ubuntu install lets you access all accounts simply by reseting passwords with any Live CD. (Hijack email accounts etc.)[/COLOR][B][COLOR=#006400]

[/COLOR][/B][COLOR=#000000]A lil pizaz gone out of that argument now tho lol[/COLOR]**[COLOR=#006400] :) [/COLOR]**

Talking about unencrypted accounts again?  Same thing happens with Windows and Mac OS.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> But I have **their** root password. Their OS doesn't know I reset it externally right?

Their root password makes absolutely no difference.  Their root user does not know your encryption key, so he cannot read your encrypted data.

If your data is encrypted using a key only the user knows, then it cannot be undone casually, in any way. The two choices a black-hat has are to brute force your encryption key, or to delete your unusable data.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> Your over simplifying there are ways software can tell what OS there running on many do it. **All** paid software that requires a license does it, with and without the internet.

So, hypothetical situation:
[LIST=1]
[*]Your system is set up with /home on its own partition.  This is pretty typical.
[*]You're using Ubuntu, the current release.
[*]Your home folder is NOT encrypted.
[*]I come along, reinstall the same version of Ubuntu, without formatting the /home partition.
[*]I have access.
[/LIST]

This is no different from changing passwords as root or from a live cd, but you're making a case that software knows what system it's running on.  It actually can get the UUID of the hard disk it's installed on, and the UUID of the disk its data is saved on, and that's about it.  Those things won't change when you reinstall. Same thing for Windows or Mac OS.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> I logged into the users that had encrypted home folders and I could open and view the files correctly.

Only the users who's passwords I reset **after** I logged back in with my **new** root password.

Did you provide the encryption password in order to see the files?  The answer is yes, or the files weren't encrypted.

---

### Post by 1clue on 2016-08-26
> **QIII said:**
> No, you haven't shown that.  You have told us what you *said* has happened.  Either you have misunderstood what you have done or something was set up improperly to begin with.

PAM (Pluggable Authentication Modules) will not allow the re-encryption of the /home/you directory passphrase in an administrative mode without providing the original password.  This is by design and it is to *prevent* exactly what you are saying you have done.  If you use the passwd command from the terminal to change your own password, your home directory passphrase is re-encrypted with your new password.


No, it's more than that.  PAM CANNOT allow the re-encryption of the $HOME directory without knowing the old passphrase.  Or rather it could re-encrypt it and then the original user could not see the files either, because first root wouold have to decrypt it and then the user would have to decrypt it.

> 
If done as an administrator, then the re-encryption can be done by issuing

```
ecryptfs-mount-private
``` with your *old password*, followed by ```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

If the simple process you are claiming were true, then you are too late in finding it.  Every Linux machine on Earth is already pwned.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> I still by my original outrage of being able to cause mayhem, lock people out, hijack email accounts on systems **without** encrypted home drives. :)

Dude.

Why do you think they came up with the idea of encrypted home folders?

All this can be done on any operating system. How do you think the FBI does its investigations?

---

### Post by 1clue on 2016-08-26
> **sudodus said:**
> This discussion made me curious, so I installed a system, and made a second user with 'encrypted home'. That second user saved a file it its home directory.

I found what I may call a glitch. After logout and login to the first user, the saved file in the second user's home directory is still available from the first user (via sudo). But after shutdown or reboot, it is not available until the second user logs in. ***So if there are more than one user in the computer, you should shutdown or reboot to clear the memory to wipe your traces***.

I also changed the password of the second user. That made it impossible to access the encryption (like it should be). I could log in to the second user, but the encrypted file (in the home directory) was not available. It complained

'Signature not found in the user keyring. Perhaps try interactive 'ecryptfs-mount-private'.

(And that works only if you have saved the passphrase for the encryption.) I could not find (and not read) the file from a live system.

I changed back to the original password of the second user, and the encrypted file was available again, when logged in as the second user.

-o-

Another alternative is 'encrypted disk' alias 'LVM with encryption'. You get as one alternative at the partitioning windows during the installation. This is what I would recommend for a laptop computer, that you use during traveling. Maybe it will be easier for you to trust such a system. But no system is 100 % safe and possible to use at the same time.


So what you're saying is that the user's password is the encryption key. I don't think that's a great idea.

---

### Post by 1clue on 2016-08-26
> **andrew.nz said:**
> I feel silly in hindsight but it seemed silly to me how easy it was to change root and sudoers passwords too so it didn't seem so far off.

Slightly off topic but is there a performance drop if someone encrypts an entire installation? When you first install a Buntu from USB or DVD there's an option.

Yes there is a performance drop. The significance of that depends on how fast your disks are, how fast your hardware is, the length of the encryption key and how heavily loaded your system is.

---

### Post by sudodus on 2016-08-26
Ubuntu installs it like this, when you select 'encrypted home' during the installation: There is a passphrase for the encryption, and it is created automatically. I think the passphrase will be encrypted and stored in the gpg keyring, and logging in [with the login password] will be enough to unlock the encryption (you need not enter the passphrase separately). So it is important to have a very good login password.

If you forget the login password, you need the passphrase or a backup.

If you install encrypted home separately (after the installation of the operating system), you can use another method, for example enter the passphrase separately - and that can make it much harder for an intruder, but also less convenient for the user.

-o-

If you use 'encrypted disk', you have to enter the passphrase to get to the login screen, or [skip the login screen and] login automatically.

There is an advantage to log in with the password - you will remember it. If you forget the login password you must create a new password, when you need elevated permissions (sudo). It is possible but not very convenient.

If you have a good passphrase for a system with encrypted disk, and you forget the passphrase, you need a backup.

-o-

Generally, good backup routines are extra important, when you use an encrypted system.

---

