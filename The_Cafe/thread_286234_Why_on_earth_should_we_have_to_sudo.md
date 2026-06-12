---
title: "Why on earth should we have to sudo?"
date: 2006-10-27
forum: The Cafe
---

### Post by Count Noobulus on 2006-10-27
I've been wrestling around with this and I don't get it. Wouldn't it be better to just embed a program directory with the created user accounts? That way anything installed on the machine (post stock install) is completely seperate from the system since it would look in the user's home program directory by default for dependencies? If anything screws up you would never have to reinstall, just remove the troublesome programs. If the program you install (again, post ubuntu installation) proves stable, you can log in as root and add it to the relevant parts of the file system to welcome it amongst stock programs... or - just root to back up the programs in the case the user account gets corrupted and nothing has to be redownloaded/or as some kind of restore feature.  

Sounds meddle proof to me. The only problem I guess is space. The necessary files that would need to be copied to the user home to make programs work during account creation is susbstantial no?

---

### Post by MedivhX on 2006-10-27
If you log in as root system becomes more vulnerable... If Windows had sudo 70% of viruses could do nothing to it...

---

### Post by Count Noobulus on 2006-10-27
Well I know that. 

What I'm saying is we shouldn't have to sudo to make significant changes to Ubuntu. Now I don't mean that everything should be done as Admin, I'm aware that's the security risk. What I'm suggesting in my first post keeps any potential problems at the user level instead of a system level in the event of a faulty app(s) install.

That's in the case the scenario I proposed is something that could work and isn't fud in my brain.

---

### Post by user1397 on 2006-10-27
the only reason thing i don't like about sudo is that everyone says its safer than a root account.  this kinda "baffles" me, cause when you are using sudo, it lasts for 15 minutes, right?  when you use a root account, it lasts until you close the terminal window.  so whats the real difference here?  as long as you close the root window, you're safe.  what, are you gonna leave your terminal window open and your computer on for days on end, until perhaps by chance, a hacker gets into your system? (which in turn is extremely unlikely)

the only advantage i see of it, is that when you are *first *typing something with sudo (so that it still requires the password), the fact that it asks for a password makes you think twice whether you should go ahead and perform that command, (like, say, sudo rm -rf /...DON'T ACTUALLY TRY THAT, IT'LL BREAK YOUR SYSTEM, YOU'VE BEEN WARNED)


while with a root account, after you log in to root, whatever command you make is automatically performed, without asking for a password.

still that doesn't even make much sense, because after you typed your password once with sudo, the root-ness is enabled for 15 minutes (this is changeable of course, but...), so after the first sudo command, everything else is potentially harmful, at least for 15 minutes.

another advantage of sudo, of course, is the fact that u don't have to remember 2 passwords.

---

### Post by DoctorMO on 2006-10-27
You can just compile the program and run from the directory it's in for most things.

to be honest sudo protects people from doing stupid things and the current setup is watch called a 'learnt by experence balance' so unless you can come up with something fantasicly fresh we'll stick with what we have

---

### Post by Count Noobulus on 2006-10-27
'You can just compile the program and run from the directory it's in for most things.'

Why isn't this done by default then.. instead of installed extras being dispersed to parts of the file system? I mean this is the potential problem with installing stuff via sudo right?

Well, if you can install something without sudo, and at the same time not compromise the file system by sticking extra stuff in there...isn't that more safe? That is what I'm ultimately getting at here. I feel misunderstood. :(

---

### Post by Brunellus on 2006-10-27
> **Count Noobulus said:**
> 'You can just compile the program and run from the directory it's in for most things.'

Why isn't this done by default then.. instead of installed extras being dispersed to parts of the file system? I mean this is the potential problem with installing stuff via sudo right?

Well, if you can install something without sudo, and at the same time not compromise the file system by sticking extra stuff in there...isn't that more safe? That is what I'm ultimately getting at here. I feel misunderstood. :(
because nobody else has linked it :[RootSudo](http://wiki.ubuntu.com/RootSudo).

We install things in /usr and /opt and so forth to make them available to all users on a system.  It is otherwise perfectly possible to execute things within your /home directory.

---

### Post by kerry_s on 2006-10-27
It's your choose, if you got a good router firewall, then you can turn off the asking for a password. just->
in terminal> sudo visudo
then change
%admin ALL=(ALL) ALL
to
%admin ALL=NOPASSWD: ALL

and you won't have to type password's any more, but you still have to use sudo.

WARNING! this is not recommended but it's up to you, it's your system. If it's any comfort i run mine with "%admin ALL=NOPASSWD: ALL"  but i also have a very good firewall i built.

---

### Post by Brunellus on 2006-10-27
> **kerry_s said:**
> It's your choose, if you got a good router firewall, then you can turn off the asking for a password. just->
in terminal> sudo visudo
then change
%admin ALL=(ALL) ALL
to
%admin ALL=NOPASSWD: ALL

and you won't have to type password's any more, but you still have to use sudo.
that is NOT RECOMMENDED.  If you want to run like this, just run Linspire.  Linspire runs all root, all the time by default.  Don't come crying when things break though.

---

### Post by Swab on 2006-10-27
> **Count Noobulus said:**
>   

Sounds meddle proof to me. The only problem I guess is space. The necessary files that would need to be copied to the user home to make programs work during account creation is susbstantial no?

Well yeah space would be an issue, especially on a multi-user system.  

I think PC BSD works a little like this, packages come compiled with all dependencies built in.

---

### Post by Swab on 2006-10-27
> **Brunellus said:**
> that is NOT RECOMMENDED.  If you want to run like this, just run Linspire.  Linspire runs all root, all the time by default.  Don't come crying when things break though.

I thought that Linspire thing was just a nasty rumour...

---

### Post by Brunellus on 2006-10-27
> **Swab said:**
> I thought that Linspire thing was just a nasty rumour...
No rumor.  My local shop was selling Linspire PCs.  CTRL+ALT+F1 got me to root@linspire #.

---

### Post by kerry_s on 2006-10-27
> **Brunellus said:**
> that is NOT RECOMMENDED.  If you want to run like this, just run Linspire.  Linspire runs all root, all the time by default.  Don't come crying when things break though.

You must of caught it while i was adding the warning :p  i pressed the submit then realized i forgot the warning. LOL

---

### Post by Brunellus on 2006-10-27
> **kerry_s said:**
> You must of caught it while i was adding the warning :p  i pressed the submit then realized i forgot the warning. LOL
I'm pretty zealous about proper user/privilege setup.

---

### Post by Count Noobulus on 2006-10-27
Well, thanks for commenting all. I wasn't trying to cause trouble, just wanted some insight and maybe help with my thoughts in some way. It just seemed to me that sudo is unnecessary for the most part.

---

### Post by Brunellus on 2006-10-27
Linux and the other Unices are the descendants of operating systems that were meant to be multi-user--you know, from back in the days that there was only *one* computer at a university or government installation.  User access and permissions in that case are pretty easy to understand:  you don't give a student the key to the faculty lounge or the principal's office.

Even if most of us use our computers in single-user situations, the least-privileged-user model is a proven way of limiting damage in the event that something should go wrong.  Think of it like watertight compartments in an ocean-going ship:  one or two compartments may flood, but the ship will not sink if the bulkheads are sealed and flooding is contained only to a few compartments.

In terms of default security and permissions, windows is a dugout canoe.  UNIX (and Linux with it) is a battleship by comparison.

---

### Post by Count Noobulus on 2006-10-27
"User access and permissions in that case are pretty easy to understand: you don't give a student the key to the faculty lounge or the principal's office."

I get the user/admin thing, I really do. But isn't what's going on in Ubuntu by default this?:

New student Billy Bob wants a slice of pie. The pie however, is in the faculty lounge. Now the faculty doesn't have a problem with giving Billy Bob temporary access because afterall...Billy Bob just wants a slice of pie. Not a big deal, it's a BIG pie. Billy's given a temporary key card rather than a master key so he can just get the slice of pie he so wants and exit. He goes in the once inaccessible lounge to get his pie, and yum - apple cinnamon. Billy Bob gets a little greedy in there and in the process of taking more than his fair slice, manages to knock the pie onto the floor. Oops. The faculty was having a party in about an hour and now the big juicy pie is gone.

They should have never given Billy Bob the key. There was no reason to. The slice of pie could have been put off to the side outside of the faculty lounge for Billy Bob to eat. Now nobody has any pie.

---

### Post by evolvedlight on 2006-10-27
I think this is the way it works:
If you unhide the files in your home directory you will see ALOT. Lots and lots and lots. These are the user specific bits, that each user can change and Should Not Affect Other Users. The other bits scattered over the system Should Not Be Changed. Unless it's network settings, for instance, that all users should have. 

So, instead of having all the bits of the program under /home/<user>/, just the User Specific Settings are under /home/<user>/. All the other bits are hidden away. Woooo. 

I, too, hated sudo when I first got into Ubuntu, but now its second nature

---

### Post by Swab on 2006-10-27
> **Count Noobulus said:**
> "User access and permissions in that case are pretty easy to understand: you don't give a student the key to the faculty lounge or the principal's office."

I get the user/admin thing, I really do. But isn't what's going on in Ubuntu by default this?:

New student Billy Bob wants a slice of pie. The pie however, is in the faculty lounge. Now the faculty doesn't have a problem with giving Billy Bob temporary access because afterall...Billy Bob just wants a slice of pie. Not a big deal, it's a BIG pie. Billy's given a temporary key card rather than a master key so he can just get the slice of pie he so wants and exit. He goes in the once inaccessible lounge to get his pie, and yum - apple cinnamon. Billy Bob gets a little greedy in there and in the process of taking more than his fair slice, manages to knock the pie onto the floor. Oops. The faculty was having a party in about an hour and now the big juicy pie is gone.

They should have never given Billy Bob the key. There was no reason to. The slice of pie could have been put off to the side outside of the faculty lounge for Billy Bob to eat. Now nobody has any pie.

But sudo access is given only to the first user by default.. the person who installed the system.  It is instead of a root account.. to stop people logging in and running as root all the time.

---

### Post by Brunellus on 2006-10-27
> **Swab said:**
> But sudo access is given only to the first user by default.. the person who installed the system.  It is instead of a root account.. to stop people logging in and running as root all the time.
As a result, first-user-sudoer is a good compromise; it allows you to run proper users and permissions, even if you're the only user on the computer.  Moving to a root/regular model means you set up *two* accounts, rather than just one.

---

### Post by Count Noobulus on 2006-10-27
Funny story. 

I was trying to install a program outside of the Ubunto depo my first week after installing Ubuntu itself. (I'm completely new to this as you know, and I've used Windows since I got my first PC in 2000). The app wasn't working properly as I was having serious permission issues (or so I thought) and shortly after - I started chown/chmodding like crazy when even after following instructions to the letter, the program didn't work...so sudo to the rescue. I was already using it, so what I was about to do couldn't hurt. I was determined to make the program work so I said fk it and chowned the entire file system to the default ubuntu and and all files world rwx. I couldn't imagine having any trouble after that, this proggy was gonna work damn it. I was convinced I had it right, mentally patting myself on the back.

Of course I was far from it, turned out I was quite the idiot, as it appeared I destroyed Ubuntu altogether! Now nothing worked. I laughed and rebooted the livecd. In that moment, I was Billy Bob and sudo should've never been in my hands. I guess that's an extreme case of a self inflicted wound, but I've read users on here talking about exploits that could be made up just for the fact that sudo is available. You'd have to get suckered into trusting an outside source I imagine. ..but 1 good deception would be all it took right?

I had no point of reference and dived in to using linux distros. Using Windows became unbearable knowing about all the rootkit stuff, so I made some kind of switch a priority. Sudoing myself to hell wasn't so bad, and I found it genuinely comical, but it should've been an easy pitfall to avoid I think. Am I the only noob to injure myself with sudo?

---

### Post by Swab on 2006-10-27
> **Count Noobulus said:**
> Funny story. 

I was trying to install a program outside of the Ubunto depo my first week after installing Ubuntu itself. (I'm completely new to this as you know, and I've used Windows since I got my first PC in 2000). The app wasn't working properly as I was having serious permission issues (or so I thought) and shortly after - I started chown/chmodding like crazy when even after following instructions to the letter, the program didn't work...so sudo to the rescue. I was already using it, so what I was about to do couldn't hurt. I was determined to make the program work so I said fk it and chowned the entire file system to the default ubuntu and and all files world rwx. I couldn't imagine having any trouble after that, this proggy was gonna work damn it. I was convinced I had it right, mentally patting myself on the back.

Of course I was far from it, turned out I was quite the idiot, as it appeared I destroyed Ubuntu altogether! Now nothing worked. I laughed and rebooted the livecd. In that moment, I was Billy Bob and sudo should've never been in my hands. I guess that's an extreme case of a self inflicted wound, but I've read users on here talking about exploits that could be made up just for the fact that sudo is available. You'd have to get suckered into trusting an outside source I imagine. ..but 1 good deception would be all it took right?

I had no point of reference and dived in to using linux distros. Using Windows became unbearable knowing about all the rootkit stuff, so I made some kind of switch a priority. Sudoing myself to hell wasn't so bad, and I found it genuinely comical, but it should've been an easy pitfall to avoid I think. Am I the only noob to injure myself with sudo?

I don´t quite get what you are saying.  Are you suggesting that you should not have complete control over your own installation?

---

### Post by Count Noobulus on 2006-10-27
No. With this thread I was trying to say to completely severe the user from root's hip by default, so if anything ever goes wrong it never goes beyond the damage of the individual user account. I'm being told that this is already the case, but I guess I'm not seeing things the same way. Maybe it's because Ubuntu has to be tweaked to behave this way, and it's not something that just works out of the box.

I think root should be locked and any modification/add-ons/added programs from the internet should be restricted to the user accounts. Everything you need would be copied to and executed from your created account and independent of root so you wouldn't have to be root to do modding/editing/install things. If anything messes up, it's only the single user account that breaks down and has no way of affecting root by proxy or other users. (I'd hope anyway, I know there are some talented crackers out there).

I think it's the same level of security, maybe better, it just takes that sudoing in the terminal out of the picture.

---

### Post by Tomosaur on 2006-10-28
I think it's about time we changed GNU/Linux to 'GNU/LNW'.

---

