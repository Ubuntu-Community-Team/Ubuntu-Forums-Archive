---
title: "A reminder about the proper way to invoke root in Ubuntu"
date: 2008-07-25
forum: The Cafe
---

### Post by aysiu on 2008-07-25
I've been answering a lot of support threads lately wherein users have said they are unable to empty the trash can because a file in there is owned by root or they cannot get a Firefox setting change to stick (and it turns out their Firefox settings folder is owned by root).

Do you know where this comes from, why this is happening?

Bad advice. It all comes from bad advice.

Please do not dispense bad advice. Dispense good advice. You probably don't realize you're dispensing bad advice, which is why I've created this reminder thread.

**A persistent root terminal prompt**
If you want a persistent root command-line instead of typing *sudo* for a series of commands, the proper way to get this persistent root is the command ```
sudo -i
``` It is *not* the command *sudo -s*.

The difference is that ```
sudo -i
``` will log you in as root and use root's environment, and *sudo -s* will log you in as root and use the user environment. That means, if you use *sudo -s*, the changes you're making will be made with root powers but affect your user folder. This is bad. You don't want this.

**Graphical root**
If you want to launch a graphical application as root, use ```
gksudo nautilus
``` or ```
kdesu konqueror
``` or (if you're using Mozilla's Firefox and need to update) ```
gksudo firefox
``` Do not use the commands *sudo nautilus* or *sudo konqueror* or *sudo firefox*.

Same deal as *sudo -i* and *sudo -s* here. If you run a graphical application with *sudo* instead of *gksudo* or *kdesu*, you'll be running the application as root but with the user's environment. That means when you move something to the trash, you'll move it to the trash as root, but it'll go into the user's trash. That means if you touch a Firefox setting, it'll be touched as root but will affect the user's Firefox setting.

**Other stuff**
Yes, I am in the habit of using *gksudo*, but I know it's a symlink to *gksu*. If you want to save yourself typing two letters, you can use *gksu* instead of *gksudo*.

*gksudo* is for GTK applications. You use *gksudo* mainly if you're using Ubuntu or Xubuntu.

*kdesu* is for QT applications. You use *kdesu* mainly if you're using Kubuntu.

**Further reading**
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by L815 on 2008-07-25
What about ?
```
sudo su
```

Leaving my question aside, very nice guide :D
I never knew about "sudo -i" or "sudo -s"

---

### Post by aysiu on 2008-07-25
> **L815 said:**
> What about ?
```
sudo su
```

Leaving my question aside, very nice guide :D
I never knew about "sudo -i" or "sudo -s"
According to [the Wiki entry on Root and Sudo](https://help.ubuntu.com/community/RootSudo#Special%20notes%20on%20sudo%20and%20shells), they're the same.

The only difference I can see is that *sudo -i* will not only log you in as root and use root's environment; it will also have the /root directory be your initial working directory. *sudo su* seems to use root's environment but keep you in the user's directory as the initial working directory.

---

### Post by L815 on 2008-07-25
Thanks for the clarification :popcorn:

---

### Post by steveneddy on 2008-07-25
I need to get into the **[COLOR="Blue"]gksudo[/COLOR]** habit myself.

---

### Post by Bachstelze on 2008-07-25
> **aysiu said:**
> The only difference I can see is that *sudo -i* will not only log you in as root and use root's environment; it will also have the /root directory be your initial working directory. *sudo su* seems to use root's environment but keep you in the user's directory as the initial working directory.

It will do more than that. [FONT="Courier New"]sudo -i[/FONT] (or [FONT="Courier New"]sudo su -[/FONT]) will *simulate an initial login*. Besides setting the environment accordingly and changing to the target user's home directory, it will also parse any files that contain commands that should be run at login-time:

```
firas@itsuki ~ % sudo cat /root/.zprofile
echo "hello world"
firas@itsuki ~ % sudo -i
hello world
itsuki ~ # exit
firas@itsuki ~ % sudo su
itsuki firas # exit
firas@itsuki ~ % sudo su -
hello world
itsuki ~ #

```

So basically, [FONT="Courier New"]sudo su -[/FONT] and [FONT="Courier New"]sudo -i[/FONT] are okay. [FONT="Courier New"]sudo su[/FONT] is also okay most of the time, but not always. [FONT="Courier New"]sudo -s[/FONT] is not.

*EDIT: added screenshot with colours for improved readability.*

*EDIT 2: oh, and for those wondering, [FONT="Courier New"]gksudo[/FONT] and [FONT="Courier New"]kdesu[/FONT] are completely interchangeable, so for example, if you have a KDE desktop, but need root powers on a Gnome app, you can very well run it with [FONT="Courier New"]kdesu[/FONT], like [FONT="Courier New"]kdesu gparted[/FONT], and don't need to install [FONT="Courier New"]gksudo[/FONT].*

---

### Post by John.Michael.Kane on 2008-07-25
Exactly why is sudo -s not okay? 

According the sudo man page.
The -S (stdin) option causes sudo to read the password from the standard input instead of the terminal device.

The -s (shell) option runs the shell specified by the SHELL environment variable if it is set or the shell as specified in passwd(5).

Neither of the above options are label as not to be used or use at your own risk.

Are there any examples of why it is wrong to use?

---

### Post by Bachstelze on 2008-07-25
> **John.Michael.Kane said:**
> 
Are there any examples of why it is wrong to use?

Which part of "commands will be run with root powers but will affect the users' personal files" do you not understand?

---

### Post by John.Michael.Kane on 2008-07-25
> **HymnToLife said:**
> Which part of "commands will be run with root powers but will affect the users' personal files" do you not understand?

As I asked are there any examples of this? Unless there is a known example of this what is posted is simply an opinion.

As a side note if you are looking for an argument you will not get one, and I will simply drop the subject.

---

### Post by Bachstelze on 2008-07-25
> **John.Michael.Kane said:**
> As a side note if you are looking for an argument you will not get one, and I will simply drop the subject.

Fine by me. But don't come crying to us when you break your account. You've been warned.

---

### Post by John.Michael.Kane on 2008-07-25
> **HymnToLife said:**
> Fine by me. But don't come crying to us when you break your account. You've been warned.

Warned about what? an opinion was given with no example offered, and a question asked, and not answered.

---

### Post by Bachstelze on 2008-07-25
> **John.Michael.Kane said:**
> Warned about what?

About the **fact** that sudo -s will let you run commands as root, but that said commands will affect **your own personal files**! Once again, what do you not understand about this?

---

### Post by John.Michael.Kane on 2008-07-25
> **HymnToLife said:**
> About the **fact** that sudo -s will let you run commands as root, but that said commands will affect **your own personal files**! Once again, what do you not understand about this?

Since your tone seems confrontational, and the talk obviously at an impasse, I will step out of this thread.

---

### Post by Bachstelze on 2008-07-25
> **John.Michael.Kane said:**
> Since your tone seems confrontational, and the talk obviously at an impasse, I will step out of this thread.

Great. Since both aysiu and I explained to you why it was bad but you refused to understand, have all sorts of fun with [FONT="Courier New"]sudo -s[/FONT] :)

And maybe now, people with valid questions can ask them.

---

### Post by Dr Small on 2008-07-25
> **aysiu said:**
> According to [the Wiki entry on Root and Sudo](https://help.ubuntu.com/community/RootSudo#Special%20notes%20on%20sudo%20and%20shells), they're the same.

The only difference I can see is that *sudo -i* will not only log you in as root and use root's environment; it will also have the /root directory be your initial working directory. *sudo su* seems to use root's environment but keep you in the user's directory as the initial working directory.
Ok. So it's not a crime if I tell someone to use 'sudo su'? :)

---

### Post by Bachstelze on 2008-07-25
> **Dr Small said:**
> Ok. So it's not a crime if I tell someone to use 'sudo su'? :)

Read post #6. *Most of the time*, it will be okay, but if for some reason the user has something in his profile files that is essential for commands to run accurately, it will not.

So, to play it safe, if you really want to use [FONT="Courier New"]su[/FONT], use [FONT="Courier New"]sudo su -[/FONT].

---

### Post by silkstone on 2008-07-25
Is there any situation in which I should **not** use sudo -i instead of sudo su?

The only time I regularly 'sudo su' is to create a tar backup of the system drive. I'm happy to use sudo -i instead (it sounds more reliable) as long as there are no snags.

EDIT/ I think you've probably answered that in the previous post while I was typing.

---

### Post by Bachstelze on 2008-07-25
> **silkstone said:**
> Is there any situation in which I should **not** use sudo -i instead of sudo su?

Yes, if you do **not** want your profile files to be source'd :) But I guess if you know enough to know when they should and should not be, you don't need to ask such questions ;)

---

### Post by aysiu on 2008-07-25
Here are some examples for you, John.Michael.Kane:
[http://ubuntuforums.org/showthread.php?p=5453598#post5453598](http://ubuntuforums.org/showthread.php?p=5453598#post5453598)
[http://ubuntuforums.org/showthread.php?p=5442891#post5442891](http://ubuntuforums.org/showthread.php?p=5442891#post5442891)
[http://ubuntuforums.org/showthread.php?p=5369069#post5369069](http://ubuntuforums.org/showthread.php?p=5369069#post5369069)

I hope that helps.

I haven't done extensive scientific testing myself, but the differences in the environments the commands use coupled with the fact that users using the less-favored commands are experiencing those problems leads me to making this thread.

---

### Post by Bachstelze on 2008-07-25
Another example that I sent to John.Michael.Kane by PM. It's the simplest I can think of, yet it proves the point very well:

*(note: don't be too puzzled about [font="courier new"]fc -W[/font], it just tells the shell to write to the history immediately, this operation being normally performed when the shell exits.)*

```
firas@nobue ~ % echo i am not root && fc -W
i am not root
firas@nobue ~ % cat .histfile
echo i am not root && fc -W
firas@nobue ~ % sudo -s
nobue ~ # echo I AM ROOT && fc -W
I AM ROOT
nobue ~ # exit
firas@nobue ~ % cat .histfile
echo i am not root && fc -W
echo I AM ROOT && fc -W
echo I AM ROOT && fc -W
exit

```

So all the commands that were run while using the root account were written in the user's history file. I hope I won't need to go into details about how this is a bad thing.

---

### Post by aysiu on 2008-07-25
Thanks for that example, HymnToLife. I don't really understand the code itself, but I understand the principle.

There may be some useful applications of *sudo -s*. I just can't think of any right now, not for a user support forum anyway.

---

### Post by voteforpedro36 on 2008-07-25
So, what about just using "su"? Maybe I missed it, but I saw using "sudo su" is okay most of the time, as well is "sudo -i", but "sudo -s" is not okay most of the time. I'm guessing su does the same thing as one of these three, am I right?

---

### Post by Bachstelze on 2008-07-25
> **voteforpedro36 said:**
> So, what about just using "su"? Maybe I missed it, but I saw using "sudo su" is okay most of the time, as well is "sudo -i", but "sudo -s" is not okay most of the time. I'm guessing su does the same thing as one of these three, am I right?

[FONT="Courier New"]su[/FONT] is not usable by default in Ubuntu. In case you enabled root logins, it does the same thing as [FONT="Courier New"]sudo su[/FONT].

---

### Post by cardinals_fan on 2008-07-25
> **aysiu said:**
> 
**A persistent root terminal prompt**
If you want a persistent root command-line instead of typing *sudo* for a series of commands, the proper way to get this persistent root is the command ```
sudo -i
``` It is *not* the command *sudo -s*.

The difference is that ```
sudo -i
``` will log you in as root and use root's environment, and *sudo -s* will log you in as root and use the user environment. That means, if you use *sudo -s*, the changes you're making will be made with root powers but affect your user folder. This is bad. You don't want this.]
Thank you.  Every time someone uses 'sudo -s', a kitten is beaten to death.

---

### Post by cardinals_fan on 2008-07-25
> **voteforpedro36 said:**
> So, what about just using "su"? Maybe I missed it, but I saw using "sudo su" is okay most of the time, as well is "sudo -i", but "sudo -s" is not okay most of the time. I'm guessing su does the same thing as one of these three, am I right?
A quick tip: add the line 'alias su="sudo -i"' to your .bashrc file.  Now you can type 'su' and it'll work fine.

EDIT: Sorry about the double post.  I didn't see the above post until it was too late ;)

---

### Post by voteforpedro36 on 2008-07-25
> **HymnToLife said:**
> [FONT="Courier New"]su[/FONT] is not usable by default in Ubuntu. In case you enabled root logins, it does the same thing as [FONT="Courier New"]sudo -s[/FONT], and therefore should be avoided. [FONT="Courier New"]su -[/font] is okay, however.

Sorry, I'm on Debian, so su is default. Thanks, I'll start using [FONT="Courier New"]su -[/FONT] now.

---

### Post by Bachstelze on 2008-07-25
> **voteforpedro36 said:**
> Sorry, I'm on Debian, so su is default. Thanks, I'll start using [FONT="Courier New"]su -[/FONT] now.

Forget what I said, I mistakenly tried that on my BSD system ;) In Ubuntu (so that should be the case in Debian too), su behaves like sudo su, which will be fine.

---

### Post by voteforpedro36 on 2008-07-25
> **HymnToLife said:**
> Dorget what I said, I mistakenly tried that on my BSD system ;) In Ubuntu (so that should be the case in Debian too), su behaves like sudo su, which will be fine.

Alrighty then. Good thing too, cause I can't get sudo to work at all on Debian.

---

### Post by Bachstelze on 2008-07-25
> **voteforpedro36 said:**
> Alrighty then. Good thing too, cause I can't get sudo to work at all on Debian.

Really ? I just couldn't live without sudo, I have it on all my systems and pretty much never use su :p

> **aysiu said:**
> Thanks for that example, HymnToLife. I don't really understand the code itself, but I understand the principle.

There was actually no need for all the fc's, the interesting part (root command written in user's history) will happen anyway when the root shell wil be exitted:

```
firas@nobue ~ % echo BEGIN EXAMPLE HERE
BEGIN EXAMPLE HERE                     
firas@nobue ~ % fc -W      # so the marker line gets written in the history
firas@nobue ~ % cat .histfile                                
echo BEGIN EXAMPLE HERE                
fc -W                                                  
firas@nobue ~ % sudo -s
nobue ~ # echo I AM ROOT
I AM ROOT
nobue ~ # exit
firas@nobue ~ % cat .histfile
echo BEGIN EXAMPLE HERE
fc -W
echo I AM ROOT
exit

```

And if you exit your normal (user) shell and open it back, you can even reasd the root commands just by pressing the up arrow, so anyone that has access to your system could see the commands you ran as root, which is an obvious security problem.

---

### Post by voteforpedro36 on 2008-07-25
> **HymnToLife said:**
> Really ? I just couldn't live without sudo, I have it on all my systems and pretty much never use su :p



There was actually no need for all the fc's, the interesting part (root command written in user's history) will happen anyway when the root shell wil be exitted:

```
firas@nobue ~ % echo BEGIN EXAMPLE HERE
BEGIN EXAMPLE HERE                     
firas@nobue ~ % fc -W      # so the marker line gets written in the history
firas@nobue ~ % cat .histfile                                
echo BEGIN EXAMPLE HERE                
fc -W                                                  
firas@nobue ~ % sudo -s
nobue ~ # echo I AM ROOT
I AM ROOT
nobue ~ # exit
firas@nobue ~ % cat .histfile
echo BEGIN EXAMPLE HERE
fc -W
echo I AM ROOT
exit

```

And if you exit your normal (user) shell and open it back, you can even reasd the root commands just by pressing the up arrow, so anyone that has access to your system could see the commands you ran as root, which is an obvious security problem.


It's a pain to have to open a terminal, run su, install an app, exit said terminal, open a new one, and open the app I installed. How safe would it be have some kind of method that would run su, then whatever I typed, then run "exit"?

---

### Post by Bachstelze on 2008-07-25
> **voteforpedro36 said:**
> It's a pain to have to open a terminal, run su, install an app, exit said terminal, open a new one, and open the app I installed. How safe would it be have some kind of method that would run su, then whatever I typed, then run "exit"?

```
su -c <command>
```

will have pretty much the same effect as

```
sudo command
```


But what I posted above only applies to *sudo -s*, not *su*. What's wrong with that?

```
% su
Password:
# apt-get install blah
[...]
# exit
% blah
```

---

### Post by aysiu on 2008-07-25
> **voteforpedro36 said:**
> It's a pain to have to open a terminal, run su, install an app, exit said terminal, open a new one, and open the app I installed. How safe would it be have some kind of method that would run su, then whatever I typed, then run "exit"?
In that particular situation, regular *sudo* would probably be the most convenient: ```
sudo apt-get install *nameofprogram*
*nameofprogram* &
``` Otherwise, you're doing ```
sudo -i
apt-get install *nameofprogram*
exit
*nameofprogram* &
```

---

### Post by smartboyathome on 2008-07-25
Maybe Ubuntu should link su to sudo -i by default, aysiu?

---

### Post by aysiu on 2008-07-25
> **smartboyathome said:**
> Maybe Ubuntu should link su to sudo -i by default, aysiu?
*su* just means *switch user*

You can *su* to another user. If you don't specify a user, it defaults to root's account.

I don't think people just come up with *sudo -s* on their own. Someone usually tells you to run *sudo -s*. So all I'm doing is just encouraging the community to espouse *sudo -i* instead.

---

### Post by ssam on 2008-07-26
I usually invoke the all powerful root, by lighting candles and chanting the four freedoms until the '$'s melt away to the holy symbol of the '#'. you need pam_séance and libouija installed.

Is this wrong?

---

### Post by koenn on 2008-07-26
> **ssam said:**
> I usually invoke the all powerful root, by lighting candles and chanting the four freedoms until the '$'s melt away to the holy symbol of the '#'. you need pam_séance and libouija installed.

Is this wrong?
It's not recommended for novice users. Candles can cause fires, and the ceremony needed to make root go away again is not very well documented.

---

