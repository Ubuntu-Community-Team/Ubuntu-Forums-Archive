---
title: "Is logging in as admin insecure?"
date: 2012-04-10
forum: Security
---

### Post by bedpotato on 2012-04-10
Hello! I recently got myself into a right old mess:

[http://ubuntuforums.org/showthread.php?t=1954590](http://ubuntuforums.org/showthread.php?t=1954590)

which is sorted now. But the reason I did it was that I remembered reading on this sticky 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

the following:

>  Limit root access (Do not log in or run programs as root). Ubuntu accomplishes this by locking the root account and the use of sudo.
Consider creating an account without sudo access for "daily use" 

That was all I was trying to do - make another account. Did I interpret that wrongly? Is there some sort of difference between a user account and a "root" account? If so, what, and how do I make a root one without locking myself out of admin access again?  

What I did was I went to settings and then clicked on user accounts and then made a new one. Was that not the kind of account being referred to in the security advice?

Thank you

Bedpotato :)

**I am a newbie so please try and dumb things down for me if you can.** Thank you. :)

---

### Post by bab1 on 2012-04-10
> **bedpotato said:**
> Hello! I recently got myself into a right old mess:

[http://ubuntuforums.org/showthread.php?t=1954590](http://ubuntuforums.org/showthread.php?t=1954590)

which is sorted now. But the reason I did it was that I remembered reading on this sticky 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

the following:



That was all I was trying to do - make another account. Did I interpret that wrongly? Is there some sort of difference between a user account and a "root" account? If so, what, and how do I make a root one without locking myself out of admin access again?  

What I did was I went to settings and then clicked on user accounts and then made a new one. Was that not the kind of account being referred to in the security advice?

Thank you

Bedpotato :)

**I am a newbie so please try and dumb things down for me if you can.** Thank you. :)When the system is installed the user *root *has no password.  The first user is given the right to assume root (admin) rights via sudo.

What you did was delete your admin rights before you created a new admin user.  Create a user that you want to have admin rights and see that that user  can use sudo BEFORE you make first user (you) an ordinary user.

On the other hand using your original user is perfectly safe.  The only time it assumes root user rights is when you sudo to give yourself rights.  The reference is for other users you might put on the system.

---

### Post by bedpotato on 2012-04-10
Thank you. I don't really understand what all of that means, but your general conclusion appears to be that it's OK for me to have just one user account and it's safe for it to have admin status. Is that correct?

---

### Post by bab1 on 2012-04-10
> **bedpotato said:**
> Thank you. I don't really understand what all of that means, but your general conclusion appears to be that it's OK for me to have just one user account and it's safe for it to have admin status. Is that correct?

You should be safe.  Use the *sudo *command wisely.  ;-)

You can have admin rights and not use them.  Linux is not like Windows. Normally you do not assign administrative rights to a mortal (regular) user on a Linux host.  The user named ***root ***has the right to do anything to the system (including trashing it).  You as a mortal user can assume those rights with the command *sudo*([COLOR="Red"]**s**[/COLOR]witch **[COLOR="Red"]u[/COLOR]**ser and **[COLOR="Red"]do[/COLOR]**).  If you don't user the command you will never give yourself root (admin as you call it) rights.

Edit:  Do some reading on how the systems works.  It will help in the long run.  Just Google Ubuntu System Administration.

---

### Post by Ms. Daisy on 2012-04-10
> Is there some sort of difference between a user account and a "root" account? Yes. Huge difference.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

That link will explain what sudo is. It will explain what root is.  It will explain how various users can use sudo to do administrative things.  (A link to this same page was also given in [post #4]("http://ubuntuforums.org/showpost.php?p=11827551&postcount=4") of your other thread.)

When I was brand-spanking-new to Linux, I found it useful to re-read my help threads.  Often I would discover that someone mentioned a link or a fact that I had missed the first time, but it was key to understanding my problem.

If you want a deep understanding you need to learn about user accounts.  See this link

[https://help.ubuntu.com/11.04/ubuntu-help/user-accounts.html](https://help.ubuntu.com/11.04/ubuntu-help/user-accounts.html)

I recommend you read all the links on that page. It's a LOT of reading.  But it's the only way to learn it.  Of course as you read and you have questions, this forum is the perfect place to ask.

---

### Post by Ms. Daisy on 2012-04-10
I'm going to say it again, partly because it's really really important, but also because numerous people have told you the same thing and I want to make sure you are hearing it.

Read the documentation.  It was created to help you understand.

---

### Post by bedpotato on 2012-04-11
Thank you, Ms Daisy. I didn't read the link you are talking about on my other thread because my other thread was not a thread about me wanting to understand. It was a thread about me wanting to fix a problem that was too hard for me. I just needed easy-to-follow instructions that I could follow without necessarily knowing what they meant, being a newbie. :)

*This* thread is more about wanting to understand so perhaps I will read the link if it's not too complicated.

Edit: I've read that link and in summary all it's really telling me is that there's something called a root account but password access to it is disabled as default anyway, because the password is locked. Therefore I still haven't the faintest idea why on earth changing the admin account affected the invisible, all-powerful thing called the root account. :confused:

bab1, it's not admin "as I call it." It's admin *as the Ubuntu settings* calls it. In this case I am not making up my own word, or carrying over a word from Windows (though I do that quite a lot I dare say)!;) In this case the terms used for user accounts in the Settings part are "Standard" and "Admin." It does not say anything about "root" there. That is why I do not understand why people kept talking about root accounts in my other thread, because I had not altered anything that was labelled as root. That's why I thought root and admin must be the same, because in changing the admin status I apparently also changed the root status. :confused:

---

### Post by haqking on 2012-04-11
> **bedpotato said:**
> Thank you, Ms Daisy. I didn't read the link you are talking about on my other thread because my other thread was not a thread about me wanting to understand. It was a thread about me wanting to fix a problem that was too hard for me. I just needed easy-to-follow instructions that I could follow without necessarily knowing what they meant, being a newbie. :)

*This* thread is more about wanting to understand so perhaps I will read the link if it's not too complicated.

Edit: I've read that link and in summary all it's really telling me is that there's something called a root account but password access to it is disabled as default anyway, because the password is locked. Therefore I still haven't the faintest idea why on earth changing the admin account affected the invisible, all-powerful thing called the root account. :confused:

bab1, it's not admin "as I call it." It's admin *as the Ubuntu settings* calls it. In this case I am not making up my own word, or carrying over a word from Windows (though I do that quite a lot I dare say)!;) In this case the terms used for user accounts in the Settings part are "Standard" and "Admin." It does not say anything about "root" there. That is why I do not understand why people kept talking about root accounts in my other thread, because I had not altered anything that was labelled as root. That's why I thought root and admin must be the same, because in changing the admin status I apparently also changed the root status. :confused:

Root is the all powerful user and owner of the system files, in Ubuntu it has no password by default and therefore locked, it can be enabled but no need really due to use of Sudo.

A admin account is a regular user who has sudo privelege or member of the sudo group which allows them to perform "root" actions by using sudo command therefore making them an administrator. (the first account on the system is usually a sudo user by default)

A regular/standard account is just that it is not root and has no admin/sudo access.

But all of this was explained in your previous solved threads, i guess you will just need to keep reading it over and over until it sticks or you come across a explanation that works.

Peace

---

### Post by bedpotato on 2012-04-11
Thank you, Haqking. I still don't understand it really. If it was explained in my other thread I think I must have missed it. There were a lot of long complicated replies that were too bewildering for me.  

How can one perform root commands if one is not really logged in as root?  Is "sudo" a sort of sneaky way of getting into the root, like using a back door?

I think I will give this one a rest now. :confused: At least my computer is working again.

Thank you for trying to help me anyway. You have been replying on a lot of my threads and I am grateful to you. :)

---

### Post by haqking on 2012-04-11
> **bedpotato said:**
> Thank you, Haqking. I still don't understand it really. If it was explained in my other thread I think I must have missed it. There were a lot of long complicated replies that were too bewildering for me.  

How can one perform root commands if one is not really logged in as root?  Is "sudo" a sort of sneaky way of getting into the root, like using a back door?

I think I will give this one a rest now. :confused: At least my computer is working again.

Thank you for trying to help me anyway. You have been replying on a lot of my threads and I am grateful to you. :)

sudo means superuser do or perform this action as the superuser (bit like at work when the boss is away they delegate tasks to a underling in their absence) sudo is a more long term thing, you are pretending to be boss.

so for example:

```
gedit
```

will open a text editor under standard access

```
gksudo gedit

```

Will open the text editor as if root did so and therefore allows you to edit system files which need root privelege for example.

If you were to unlock the root account (it is not disabled but locked from access) then you could login as root and

```
gedit
```

would work the same as

```
gksudo gedit
```

as you are logged in as root.

Now i used **gk**sudo as **gk**sudo should be used for graphical apps, sudo shoudl be used for text based apps such as

```
sudo nano
```
```
sudo vi
```
```
sudo apt-get install
```

But if you say wanted to open your file manager nautilus from the terminal with root privelege say to access files you cant see with standard permission as it is a graphical app then you should use

```
gksudo nautilus
```

as it is graphical

No need however to unlock it or login with it as we can delegate root tasks and power to users by putting them in the sudo group and when they need to perform a root action they append sudo to the command.

Every other time they are running as standard user and therefore less chance of doing something silly/stupid which can break the system.

Everytime you use sudo it will ask for a password, which is your own regular login password which just lets you confirm that you want to perform the action requested.

If the system asks for a root password then enter your own login password or if root is enabled the password you assigned to it, but like i said no need to enable root, just use sudo or gksudo.

there is no gksudo group, being in the sudo group allows you to modify sudo command by saying i want a graphical app which is where we use gksudo

There is more to it that i could add but this is about as simple as i can make it.


Peace

---

### Post by darkod on 2012-04-11
The really short answer is: The first user created has admin rights but only by typing 'sudo' in front of the command, or 'gksu' in front of commands using GUI program.

That way it uses admin permissions temporarily and ONLY for the commands that you use combined with sudo. That protects you from unintentionally running commands with admin permissions.

While in windows once you log in as admin you have max permissions for everything you do, in ubuntu you log in with your "normal" user and use 'sudo <command>' only when you need to run something with admin permissions.

The above assumes we are talking about the first user created during the install. Only that user has sudo rights by defauls. For users created later, you have to give them that right.

---

### Post by haqking on 2012-04-11
> **darkod said:**
> The really short answer is: The first user created has admin rights but only by typing 'sudo' in front of the command, or 'gksu' in front of commands using GUI program.

That way it uses admin permissions temporarily and ONLY for the commands that you use combined with sudo. That protects you from unintentionally running commands with admin permissions.

**While in windows once you log in as admin you have max permissions for everything you do**, in ubuntu you log in with your "normal" user and use 'sudo <command>' only when you need to run something with admin permissions.

The above assumes we are talking about the first user created during the install. Only that user has sudo rights by defauls. For users created later, you have to give them that right.

I dont want to complicate things, (but then i normally do ;-)

But that is only true if you choose too which is the same as in Linux really.

You can login to windows as a standard user and then right click on a icon/exe and open as administrator (like using gksudo)

and from command prompt you use ```
runas
``` to perform admin action like using sudo.

It is just that not many windows users know that and if they do dont bother using it. And by default the first user is a admin user

Least privelege should be used at all times.

By the way i am not picking at your post, more clarifying for others reading and hopefully more people will start using least privelege.

Peace

---

### Post by Morbius1 on 2012-04-11
> How can one perform root commands if one is not really logged in as  root?  Is "sudo" a sort of sneaky way of getting into the root, like  using a back door?The thing I think that makes this confusing from a Windows' user's perspective is the unfortunate use of the word "administrator" in Linux. The "administrator" in Windows is in fact root. The "administrator" in Linux is not.

Root is the master of your OS. The first user on Linux has rights  bestowed upon it by root to "run as root" so he can perform actions as  root to accomplish certain tasks and for a limited amount of time. The "standard user" or subsequent users have no such rights bestowed upon him.

---

### Post by haqking on 2012-04-11
> **Morbius1 said:**
> The thing I think that makes this confusing from a Windows' user's perspective is the unfortunate use of the word "administrator" in Linux. The "administrator" in Windows is in fact root. The "administrator" in Linux is not.

Root is the master of your OS. The first user on Linux has rights  bestowed upon it by root to "run as root" so he can perform actions as  root to accomplish certain tasks and for a limited amount of time. The "standard user" or **subsequent users have no such rights bestowed upon him.**

Though they can be given, just for clarity.

Also Administrator in Windows has root access, but is not root, as root is a single user and cant be more than one, you can have multiple administrators on a windows box all with root like access.

On linux only one UID of 0

On windows multiple -500 SIDS can exist or begin with S-1-5

But in my effort for clarity and completeness i may be over complicating things again ;-)

---

### Post by winh8r on 2012-04-11
A fairly simple analogy to explain how the root/sudo thing works.

Imagine Ubuntu to be a Rock Concert

The person running the concert is Root, he has all the power to make things happen anywhere in the whole event. Root is the Boss (**[COLOR="Red"]this is who root is in Ubuntu[/COLOR]**)

Root makes sure that the event is secure  and that no-one can change the way things are being run without his agreement or knowledge by issuing stage passes to 

everyone who is involved in the running of the concert.

**[COLOR="Red"]These stage passes are like admin rights in Ubuntu[/COLOR]**. Some people need them and are issued with them whilst others are not allowed them under any circumstances.

The first group to get stage passes are the event staff, **[COLOR="Red"]they are the equivalent of the admin users group on Ubuntu[/COLOR]**, they can go around freely but when they get to 

an area that is restricted by security they will be denied access unless they use the word "sudo" and give the correct password.


So when the stagehand needs to go the backstage area he gets to the securtiy gate and says " backstage". The security guy says "NO ACCESS" , so the stagehand has 

to say "sudo backstage". This tells the security guy to check the list he has been given by Root and see if the stagehand is authorised to get backstage by using 

this command. The stagehand has  his name  on the list of authorised people ( **[COLOR="Red"]in the sudoers file in Ubuntu terms[/COLOR]**)  issued by Root (the Boss) and so is allowed 

access to the backstage area after giving his password to the security guy. The stagehand can now alter things in the backstage area as he has Roots permission to 

be there and to carry out actions there. 

When he has finished doing what he is there to do, he goes back to just being a stagehand and has no special privileges until he acquires them again by using the "sudo" command again and giving the correct password at the next security gate he needs to get through.


This method means that Root is in control at all times, and no-one can change the way things are being run unless Root has specifically allowed them to have his permission by using the "sudo" command and using their password. If you are not on the list, then you are not allowed in.

Now we look at the fans at the concert, **[COLOR="Red"]they are like the standard users group in Ubuntu[/COLOR]**, they are allowed in to the venue to see the concert but have restrictions on where they can go.

If a fan tries to get to the backstage area , she approaches the security gate and says " backstage" , the security guy says "NO ACCESS" so she tries to get in by 


saying "sudo backstage", at this point the security guy takes her name and checks the list he was given by the boss (Root), he does not see the fan on the list and 

so says to her "NO ACCESS" , he then tells her that this incident will be reported to Root because she has tried  get into somewhere she is not allowed to go by using the "sudo" command when her name is not on the list of people who are allowed to use the "sudo" command. (**[COLOR="Red"]this is the message you see in Ubuntu that says "access denied, user is not in the sudoers file, this incident will be reported"[/COLOR]**)

This is a very basic analogy but hopefully might make it easier to see how the basics work.

---

### Post by bedpotato on 2012-04-11
Oh thank you everyone! Especially Haqking and Winh8r :)

I will keep reading it over and over again and hopefully like Haqking has said it will just suddenly sink in. Thank you to everyone for going to the trouble of trying to explain it to me.

---

### Post by darkod on 2012-04-11
> **haqking said:**
> I dont want to complicate things, (but then i normally do ;-)

But that is only true if you choose too which is the same as in Linux really.

You can login to windows as a standard user and then right click on a icon/exe and open as administrator (like using gksudo)

and from command prompt you use ```
runas
``` to perform admin action like using sudo.

It is just that not many windows users know that and if they do dont bother using it. And by default the first user is a admin user

Least privelege should be used at all times.

By the way i am not picking at your post, more clarifying for others reading and hopefully more people will start using least privelege.

Peace

First of all, the OP said himself he is very confused and new, so widening the subject is doing more harm than good. :)

But having said that, I simply have to say that there is a significant difference, at least in my eyes.

Yes, right-click, Run As Administrator exists in windows, but that is mostly to overcome UAC limitations since Vista. In XP it also exists as Run As if you are in a domain (XP Pro).

But for me that is definitely not the same. You could open the Run As Administrator but if you are not a local (or domain) administrator, it will ask you for a username that has admin permissions, not just to retype your own password.
So, as I said, if you ARE an administrator, once logged in you have "the power" right away. Very rarely you will use Run As.
And if you ARE NOT an administrator, you can't simply elevate yourself to that level by using Run As otherwise having different types of accounts would be pointless. You would need to use another username, not your own.

In ubuntu you use 'sudo' sort of as confirmation, as I see it, to achieve tasks that need higher level of permissions. And it asks you for your own password. Granted, same as in windows, if you are not part of sudoers (admin), you can't simply become admin, regardless if you try with 'sudo' or not.

So, with ubuntu, you are sort of a hidden administrator and the 'sudo' brings it out of you. In windows you are either administrator from the start (login), or not, and you can't change that.

---

### Post by Morbius1 on 2012-04-11
Let us not forget how this all started:
> I had just one user account on Ubuntu and it was set to be the admin  one. I remembered reading that it wasn't a good idea to be always logged  in as admin, so I decided I would change that account to "Standard."  Fine. I also changed the password on it to something more secure.Except for the actual changing of the Linux admin account to a standard one instead of adding another account and marking it as "standard" she did everything by the book as far as **Windows** is concerned:
> What is an administrator account?

An administrator account is a user account that lets you make changes that will affect other users. Administrators can change security settings, install software and hardware, and access all files on the computer. Administrators can also make changes to other user accounts.

When you set up Windows, you'll be required to create a user account. This account is an administrator account that allows you to set up your computer and install any programs that you would like to use. Once you have finished setting up your computer, we recommend that you use a standard user account for your day-to-day computing. It's more secure to use a standard user account instead of an administrator account.So the question of this topic was:
> Is logging in as admin insecure?No. Being admin  in Linux is different from being admin in Windows.

If I want to add software on Windows as an administrator I automatically have the permissions to do that. In Linux as an admin user I also have permissions to do that but I have to prove to root that I can by giving it a password.

---

### Post by haqking on 2012-04-11
> **darkod said:**
> First of all, the OP said himself he is very confused and new, so widening the subject is doing more harm than good. :)

But having said that, I simply have to say that there is a significant difference, at least in my eyes.

Yes, right-click, Run As Administrator exists in windows, but that is mostly to overcome UAC limitations since Vista. In XP it also exists as Run As if you are in a domain (XP Pro).

But for me that is definitely not the same. You could open the Run As Administrator but if you are not a local (or domain) administrator, it will ask you for a username that has admin permissions, not just to retype your own password.
So, as I said, if you ARE an administrator, once logged in you have "the power" right away. Very rarely you will use Run As.
And if you ARE NOT an administrator, you can't simply elevate yourself to that level by using Run As otherwise having different types of accounts would be pointless. You would need to use another username, not your own.

In ubuntu you use 'sudo' sort of as confirmation, as I see it, to achieve tasks that need higher level of permissions. And it asks you for your own password. Granted, same as in windows, if you are not part of sudoers (admin), you can't simply become admin, regardless if you try with 'sudo' or not.

So, with ubuntu, you are sort of a hidden administrator and the 'sudo' brings it out of you. In windows you are either administrator from the start (login), or not, and you can't change that.


well to me.

Runas allows a user to run specific tools and programs with different permissions than the user's current logon provides.

Sudo allows a user to run specific tools and programs with different permissions than the user's current logon provides, except that current user login has permission to use sudo.

Seems the same to me ;-)

But i guess we are getting into opinion and semantics.

and runas has been in all versions of windows since windows 2000 and you dont need XP pro or a domain to use it.

But yes sudo uses same account where as runas doesnt.

However runas can run as any user, su can do that also.

And yes you need to know the account as you would with su. (yes i know su is not same as sudo)

but yes for sudo it is same account.

And in Windows i dont agree you are either administrator from login or not, thats one of the points of of runas to use least privelege so you can login with non admin account but perform admin action by supplying admin credentials.

But i think you are right, i am over complicating this thread.

I think we will leave it there now as its been covered and going off track.

Peace

---

### Post by CharlesA on 2012-04-11
I doubt this will help any, but I'll just leave it here in case. ;)

[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by winh8r on 2012-04-11
> **CharlesA said:**
> I doubt this will help any, but I'll just leave it here in case. ;)

[http://xkcd.com/149/](http://xkcd.com/149/)


It helped! :lol:

---

### Post by bedpotato on 2012-04-12
That's really cool! It would make a good avatar. :lolflag:

---

