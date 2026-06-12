---
title: "Basic Security and Maintenance FAQ for Windows Users"
date: 2007-12-14
forum: The Cafe
---

### Post by thelatinist on 2007-12-14
[*Please note: this is a first draft of an FAQ I wrote up with people migrating from Windows in mind.  In my experience, such people very often ask the same few questions about basic maintenance over and over again.  If you have any corrections, suggestions, additions, etc., please post them and I will work them into the thread.*]

People migrating from windows have a special set of concerns stemming from years running an insecure and poorly-designed operating system.  This FAQ is designed to answer some of the most frequently asked questions about security and maintenance in Linux, namely:
[LIST=1]
[*]How do I install Anti-virus Software?
[*]How do I install a firewall?
[*]How do I configure the firewall? 
[*]How do I get Firestarter to run automatically at startup?
[*]How do I defragment my hard drive?
[*]What am I going to do with all the time I used to spend doing Windows maintenance?
[/LIST]

**How do I install Anti-virus Software?**

You probably do not need anti-virus software unless you want to use it to check a windows computer over a network.  There are no serious Linux viruses in the wild, and if you follow simple precautions like only downloading software from trusted sources you will not get any viruses.  Nor do you have to worry about passing on Windows viruses to your friends unless you do something foolish like forward an attachment your receive in email.  As strange as it may seem to someone coming from Windows, you don't need to install tons of software to secure your computer under Linux: Linux is secure by design.

**How do I install a Firewall?**

You do not need to install a firewall because Linux has one already built in, called iptables!  Again, adding bloated software to a fresh install just to make it secure is the old Windows model.  If you are using Ubuntu while reading this, iptables is running in the background, protecting you with a default configuration. For most people, this default will be enough.  If you need to customize the firewall's rules or close specific ports, that is easy to do.

**How do I configure the Firewall?**

In most cases you don't need to!  A default Ubuntu installation does not include any software that is listening for incoming connections.  If you have a static ip address or if you install server software on your computer, you will probably want to configure custom rules for handling incoming connections.  The easiest way to configure iptables is probably to use Firestarter, a GUI utility which is available in Applications > Add/Remove... or through your favorite package manager.  Firestarter will walk you through closing ports and provides an easy way to configure other rules.  When you are done configuring, simply close Firestarter.  Iptables will continue to run silently in the background.

**How do I get Firestarter to run automatically at startup?**

You do not need to keep Firestarter running.  Once iptables is configured, your computer will be protected.  You only need to run Firestarter again if you want to change your firewall settings (e.g., to open a port you previously closed).

**How do I defragment my hard drive?**

Again, you don't need to!  Linux uses a file system called ext3 which is much more careful about its placement of files.  Basically, it leaves room for files to grow so that they don't become fragmented.  If a file should become fragmented, the drive will naturally defragment as you save and delete files.  There just isn't a need for regular disk maintenance to keep your system running efficiently.  If you dual boot, you will have to do any defragmentation on your NTFS partitions from within Windows.

**What am I going to do with all the time I used to spend doing maintenance on my operating system?**

That's up to you, but can I suggest you spend a little of it giving back to the community at [http://www.ubuntuforums.com/](http://www.ubuntuforums.com/)?

---

### Post by Bruce M. on 2007-12-14
If I may suggest

Identify "iptables" as the default firewall in the first sentence of **How do I install a Firewall**, like this:

> You do not need to install a firewall because Linux has one already built in, *iptables*! If you are using Ubuntu while reading this, *iptables* is running in the background, protecting you with a default configuration.

Then you continued with:  **How do I get Firestarter to run automatically at startup** A new user *might* think:  What's Firestarter?

As a suggestion change it to this:

> **Configuring Iptables**

There is a GUI program to help you configure *iptables* called **Firestarter**, and that is all it does, if you feel you need a custom configuration. Once *iptables* is configured to your liking, your computer will be protected as it runs automatically every time you login to Ubuntu..  You only need to run Firestarter again if you want to change your settings (e.g., to open a port you previously closed). Rest assured, *iptables* is running.

Note:  It still amazes me that I do not need to defrag my hard drive with Ubuntu.  Very refreshing to say the least.

Hope this helps.

---

### Post by siciliancasanova on 2007-12-14
If I may add.

If you are just using Ubuntu for personal use and your ISP is giving you a dynamic IP address you really don't have to do anything besides following general precautions when browsing the web which you should always follow no matter what machine you're on.

If you have a static IP address, you have a server available for the web, (unknown people entering your network) or have your machine set up for SSH, there are definitely some security precautions you need to take.

---

### Post by thelatinist on 2007-12-15
I've made some changes based on your suggestions.  Any further input would be appreciated.

---

### Post by RomeReactor on 2007-12-15
Hi. Very good post. My only suggestion would be to explain that software installation can be done through Syanptic or Add/Remove, instead of endlessly searching the web for places to download programs, and how updating those programs is done automatically.

---

### Post by antharr on 2007-12-15
I love not having to bloat my OS with software just to secure it. This was a very big reason I had to get away from Windoze. I would do a fresh install and everything is running nicely until I install anti-virus, anti-spyware software, and a firewall. I got so sick of it. This is also my main selling point when suggesting someone to move over to Linux for a test run. I perform the tasks I need to do and just let the computer run for weeks with no shutdowns or restarts.

---

### Post by autocrosser on 2007-12-15
Very good post!! Might add that the system will do fsck every 30 starts--I  normally modify my rcS to autofix any errors found:

                                   

                                          ***_ HOWTO - Fix any filesystem errors found on boot automatically_***
    [LEFT]***_Edit /etc/default/rcS to have:_***[/LEFT]
    
    [LEFT]***_FSCKFIX=yes_***[/LEFT]
    
    [LEFT]***_Then any errors found will be fixed automatically._***[/LEFT]

---

### Post by Jack78 on 2007-12-15
Really highlights the advantages of Ubuntu for former Windows users - it's all there out-of-the-box :).

---

### Post by Pierrot Lafouine on 2008-03-31
Hi
This post is for me :lolflag:  I'm dos/windows user for too much time (since DOS 3.3)

I installed Ubuntu couple weeks ago.
I had hard time to configure Ethernet stuff, as my modem was PPPoE.
I had to find how to run PPPoEConf.
Would be nice to add Ethernet part to this useful post.
This post should be read by all windows users.
My 2 cents opinion

Cheers!

---

### Post by udh on 2008-04-01
My question is about **Defragmentation of windows drive**.
Will it be harmful to Ubuntu installation if I use a program like Diskeeper to defrag from Windows? I read somewhere that doing so-Diskeeper modifies MBR and then everything(GRUB+MBR) are screwed up.:confused: I just want to make sure "defragmenting from windows doesn't harm Ubuntu". Please clarify..:popcorn:

---

### Post by udh on 2008-04-14
> **udh said:**
> My question is about **Defragmentation of windows drive**.
Will it be harmful to Ubuntu installation if I use a program like Diskeeper to defrag from Windows? I read somewhere that doing so-Diskeeper modifies MBR and then everything(GRUB+MBR) are screwed up.:confused: I just want to make sure "defragmenting from windows doesn't harm Ubuntu". Please clarify..:popcorn:


I had expected somebody to reply on this, please.:confused: I am getting my windows slower day by day. It is not possible for me to give up windows suddenly.:( Though I am learning each day to find substitutes for windows applications & make it extinct sooner:guitar:

---

### Post by Tatty on 2008-04-14
> **udh said:**
> My question is about **Defragmentation of windows drive**.
Will it be harmful to Ubuntu installation if I use a program like Diskeeper to defrag from Windows? I read somewhere that doing so-Diskeeper modifies MBR and then everything(GRUB+MBR) are screwed up.:confused: I just want to make sure "defragmenting from windows doesn't harm Ubuntu". Please clarify..:popcorn:

You do definately mean defragging your windows partition dont you?  Trying to use that software to defrag your Ubuntu partition will not work.

As for it messing with the MBR, I do not see any real reason for it to do this, but I have never used this software so i couldnt really say.  If i were you i would just try it.  If It does happen to re-write your MBR, you can always re-install grub using either the Ubuntu Live CD or the SuperGrub CD.

You could always use the defragger that ships with windows.  I know it is well known to be rather sub-standard at its job, but overall it does work.  Give it three or four passes and your system should be pretty well defragged for general purposes.

---

### Post by udh on 2008-04-14
> **Tatty said:**
> You do definately mean defragging your windows partition dont you?  Trying to use that software to defrag your Ubuntu partition will not work.

As for it messing with the MBR, I do not see any real reason for it to do this, but I have never used this software so i couldnt really say.  If i were you i would just try it.  If It does happen to re-write your MBR, you can always re-install grub using either the Ubuntu Live CD or the SuperGrub CD.

You could always use the defragger that ships with windows.  I know it is well known to be rather sub-standard at its job, but overall it does work.  Give it three or four passes and your system should be pretty well defragged for general purposes.

thanks tatty, exactly, i wanted to use windows defrag application in windows to defrag windows drives. but as I have only one drive on which everything including ubuntu is installed, i wasn't sure if i should defrag in windows, for reasons i had mentioned earlier.

anyway, the real problem now is i tried to run defrag, but my defrag tool (diskeeper) in windows is disabled since the time i installed ubuntu. Apparently I will need to tweak something in windows. tht's another issue.

I have ubuntu installation CD so, thanks for that advice, I will try that in case MBR or grub gets corrupted.:)

---

### Post by hyper_ch on 2008-04-14
I like that you stress that AV and FW is not needed or rather leave it in the state that it is :)

---

### Post by scorp123 on 2008-04-14
> **thelatinist said:**
>  **How do I install a Firewall?**

You do not need to install a firewall because Linux has one already built in, called iptables!  Again, adding bloated software to a fresh install just to make it secure is the old Windows model.  If you are using Ubuntu while reading this, iptables is running in the background, protecting you with a default configuration.  iptables is not active per default, it doesn't do anything. It doesn't need to. Per default there is no server process that would require this kind of protection. Your statement about "iptables running in the background" (where in fact it does nothing whatsoever unless you tell it do to something!) "protecting" a user with a "default configuration" is **false.** It simply isn't true and quite misleading.

**The default configuration of iptables on Ubuntu is "do nothing".** That may be strange for a Windows user but it's perfectly OK. Again: different than on Windows there are no network services whatsoever running per default (Windows on the other hand has tons of these!) that would need a firewall to protect them. So that's why iptables does nothing in its default configuration: network-wise there is nothing to protect on a default setup.

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> Your statement about "iptables running in the background" (where in fact it does nothing whatsoever unless you tell it do to something!) "protecting" a user with a "default configuration" is **false.**
This is false... as you have said that by default iptables is unconfigured - hence allow everything... as a necessity for iptables actually to allow anything/everything it has to run... something that does not run, cannot allow something ;)
So the statements are correct and with the default configuration users are protected.

---

### Post by zakirs on 2008-04-14
AWSOME post dude :D

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  as a necessity for iptables actually to allow anything/everything it has to run...  iptables is part of the kernel, so yes, it's kinda there, but it is not a special daemon or program that the user can click on and voila, "it's there". The description made by OP is misleading. That's what I meant, so nope, my statement wasn't false.

> **hyper_ch said:**
>  So the statements are correct and with the default configuration users are protected.  That whole sentence is misleading too. It suggests that the user is somehow actively being "protected" by iptables when in fact he is not (unless the user tells it to become active and start blocking stuff). The default setup of Ubuntu is secure because there is nothing that would accept incoming connections and not because iptables does some mysterious magic out of the box by "being there in the background" (or not).

---

### Post by hyper_ch on 2008-04-14
you don't seem to differentiate between misleading and false... but you should

And then my statement is correct... with the default configuration iptables does everything required to protect the user... in that specific content it means it does nothing ;)

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
> you don't seem to differentiate between misleading and false... but you should  If something is misleading it isn't right. Thus it is false. 1 or 0. ;)

---

### Post by MaxVK on 2008-04-14
As a windows user who has moved entirely to Ubuntu since January this year I can say that this post is very helpful - I asked most of these questions myself, and the answers I got are pretty much what is here in this post.

Arguing about the semantics of the statements is a waste of time - As long as ex-Windows users can understand the basics and answer their questions its fine - they can pick up the finer details as they go along. Knowing that you are essentially safe from attack or infection gives you a chance to stop panicking and get into the proper Linux mindset.

Regards

Max

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> If something is misleading it isn't right. Thus it is false. 1 or 0. ;)

that is false... misleading does not necessarily mean it's not right...

Something can be misleading inadvertently... and just because it may be appear to be misleading for you it may not appear to everyone... however, it still does not make it false.

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  that is false... misleading does not necessarily mean it's not right...  It leads to false conclusions. Hence: false.

> **hyper_ch said:**
>  Something can be misleading inadvertently... and just because it may be appear to be misleading for you it may not appear to everyone... however, it still does not make it false.  Your fuzzy logic here will only confuse newcomers who want to know whether or not they need a firewall. And please read OP's posting again. He didn't say anything about the "default configuration" being safe or not. What he wrote was this:

"If you are using Ubuntu while reading this, iptables is running in the background, protecting you with a default configuration."

And no twisting of words of yours will make that sentence correct, especially the latter part of the sentence. Out of the box iptables is protecting nothing and nobody (it doesn't need to), hence the part "[iptables is] protecting you with a default configuration" is false.

Now if you could stop your word plays and check OP's posting again for other inaccuracies (because making such a posting is in fact a good idea and should be supported)? Thank you.

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> It leads to false conclusions. Hence: false.
In your perception it does :) but you are not everybody... as misleading implies, it does not always lead to false conclusions.

> **scorp123 said:**
> Your fuzzy logic here will only confuse newcomers who want to know whether or not they need a firewall.
Vice-versa ;) The OP was quite clear that nothing needs to be done... you did actually expand the issue into a more complex one ;) so this means you actually were the one that confuses newcomers ;)

> **scorp123 said:**
> And please read OP's posting again. He didn't say anything about the "default configuration" being safe or not. What he wrote was this:

"If you are using Ubuntu while reading this, iptables is running in the background, protecting you with a default configuration."

And no twisting of words of yours will make that sentence correct, especially the latter part of the sentence. Out of the box iptables is protecting nothing and nobody (it doesn't need to), hence the part "[iptables is] protecting you with a default configuration" is false.
And it's not twisting of words but reading what is written there ;) And besidesl, iptables still protects a user with a default configuration, even when that default configuration does nothing... you can't change the truth of that ;)


> **scorp123 said:**
> Now if you could stop your word plays and check OP's posting again for other inaccuracies (because making such a posting is in fact a good idea and should be supported)? Thank you.
Same goes for you ;)

---

### Post by Hallvor on 2008-04-14
Yes. IPtables does not protect anything at all out of the box. 

Just run 

```
iptables -L
``` to show an active rule set. If there aren`t any, there is no firewall.

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  The OP was quite clear that nothing needs to be done...  Even though that part is correct the explanation he gives is false, though. Again: Ubuntu is safe out of the box because there is nothing that accepts incoming network connections, not because there is a firewall of any sorts.

> **hyper_ch said:**
>  you did actually expand the issue into a more complex one ;) so this means you actually were the one that confuses newcomers ;)  I am giving more precision to the why and how. Believe it or not, but there are newcomers out there who care about such things, they want to know why something is "safe" or isn't. Telling people that they are "safe" because "there is a firewall" (which does nothing whatsoever unless you tell it to do something!) is false and it's wrong to give people a completely false sense of security with such unprecise explanations.

> **hyper_ch said:**
>  And besidesl, iptables still protects a user with a default configuration, even when that default configuration does nothing... **That's complete and utter nonsense!** How can it protect ***anything*** if there are **no rulesets** in the "default configuration" that would tell it to do anything? **Hence there is no protection from iptables.**

Stop posting BS please, OK?

---

### Post by scorp123 on 2008-04-14
> **Hallvor said:**
> Yes. IPtables does not protect anything at all out of the box.  Just run  ```
iptables -L
``` to show an active rule set. If there aren`t any, there is no firewall. Exactly my point! Thank you.

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> Even though that part is correct the explanation he gives is false, though.
He gives no false explanations ;)

> **scorp123 said:**
> I am giving more precision to the why and how. Believe it or not, but there are newcomers out there who care about such things, they want to know why something is "safe" or isn't.
Those who want to know more will look it up themselves or ask for it... but the majority is just content when they achieve to get their computers up and running... so you do not really do them a favour.

> **scorp123 said:**
> Telling people that they are "safe" because "there is a firewall" (which does nothing whatsoever unless you tell it to do something!) is false and it's wrong to give people a completely false sense of security with such unprecise explanations.
I could clarify and say telling users they are safe if they do this or that is equally false... security is a continuing process... but as said, for newcomers they are happy if there's a reasonable amount of security AND if everything works...

> **scorp123 said:**
> **That's complete and utter nonsense!** How can it protect ***anything*** if there are **no rulesets** in the "default configuration" that would tell it to do anything? **Hence there is no protection from iptables.**
iptables works as firewall... or rather package filtering... and it does its job according to the ruleset ;) so if you set no rules then it does its job according to that... so if someone decides to put 100 rules in it iptables will filter and secure according to those rules... if someone decides not to put anything in it, iptables will filter and secure according to those rules...

> **scorp123 said:**
> Stop posting BS please, OK?
As soon as you do and as soon as you stop confusing newcomers...

Basically the way the OP created it,it's fine for newcomers... your view will be more detailed and not be useful for newcomers... my views here again is a finer grain on yours ;) but that's meanwhile way too complex for any newcomers...

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  He gives no false explanations ;)  He does. So do you. :(

> **hyper_ch said:**
>  ... so you do not really do them a favour.  Believe it or not, but I do. See MaxVK's posting above: "... Knowing that you are essentially safe from attack ... "  <= that's only true for as long as he doesn't install anything that would accept network connections. As soon as he installs OpenSSH, Apache or Samba (and some newbies do *exactly* that!) that part isn't true anymore. He can be attacked. And iptables will do *nothing* to stop that and offer no protection (regardless of your silly interpretation about what a ruleset is or isn't!) unless he takes care of the problem and defines a ruleset himself.

> **hyper_ch said:**
>  iptables works as firewall... or rather package filtering... and it does its job according to the ruleset ;)  And per default there is no ruleset and thus iptables does nothing whatsoever. Especially: It does *NOT* protect the user's machine in any way.

> **hyper_ch said:**
>   if someone decides not to put anything in it, iptables will filter and secure according to those rules... Your logic is deeply flawed. If there are no rulesets whatsoever (check with "sudo iptables -L") there are no rules whatsoever and there is no filtering and no securing whatsoever!

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> He does. So do you. :(


> **scorp123 said:**
> Believe it or not, but I do. See MaxVK's posting above: "... Knowing that you are essentially safe from attack ... "  <= that's only true for as long as he doesn't install anything that would accept network connections. As soon as he installs OpenSSH, Apache or Samba (and some newbies do *exactly* that!) that part isn't true anymore. He can be attacked. And iptables will do *nothing* to stop that and offer no protection (regardless of your silly interpretation about what a ruleset is or isn't!) unless he takes care of the problem and defines a ruleset himself.
You have wrong assumptions here...
(1) an attack can always come... the only way to prevent it is to unplug yourself from the net and deposit your computer in a bank's tresor vault...
(2) iptables will exactely do what it is configured to... by adding someting new you'll also have to edit iptables...
(3) ... but (2) depends again on your network structure :) it is most likely people are already firewalled through the modem/router... and if not, meaning if they are on dial-up then (a) they won't be online 24/7 and (b) when they are online they'll have a different ip
(4) you do take presumptions that they install something... some do... but most don't...
(5) insulting your opponent does not make your arguments stronger, but weaker... think about that..

> **scorp123 said:**
> 
 And per default there is no ruleset and thus iptables does nothing whatsoever. Especially: It does *NOT* protect the user's machine in any way.
iptables does what it is supposed to do :) that is true for any firewall... - assuming that iptables can be called a firewall
- iptables is running upon boot
- iptables runs its rules
--> iptables does what it is told to do and ensures protection to that level

As said, that's an abstraction layer more deeper than yours...

Besides: this is about BASIC security... you are confusing the newcomers in here ;)

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  (2) iptables will exactely do what it is configured to... by adding someting new you'll also have to edit iptables... Thank you, that was my point exactly. **Per default it _isn't configured_ and hence it does _nothing._ [COLOR="Red"]And because it does nothing it offers no security whatsoever "out of the box".[/COLOR]** Hence OP's explanation he gives is false ... or at least very unprecise.

And I don't mind abstract thinking but you are really just twisting words and facts around and confusing the cr*p out of everyone. That's not "abstract thinking", especially if you claim untrue things like "iptables protects users anyway even if there are no rulesets" .... [COLOR="Red"]How is that supposed to help anyone?[/COLOR]

If anyone falls for the stuff you wrote up there and anything bad happens to them afterwards it will be your fault.

Someone should report this thread to the admins here, let's see what they think about your "abstract thinking" and giving people a false sense of security for the wrong reasons?

In any case I am stopping here and "good luck" to anyone blindly believing what you and OP wrote up there.

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> Thank you, that was my point exactly. [B]Per default it _isn't configured_ and hence it does _nothing._ 
It is configured - to do nothing... but still is ;)

> **scorp123 said:**
> And because it does nothing it offers no security whatsoever "out of the box".[/COLOR][/B] Hence OP's explanation he gives is false ... or at least very unprecise.
It offers protection according to its configuration... still the OP is not false ;)

> **scorp123 said:**
> And I don't mind abstract thinking but you are really just twisting words and facts around and confusing the cr*p out of everyone.
Actually, that's what you've been doing all the way...

> **scorp123 said:**
> That's not "abstract thinking", especially if you claim untrue things like "iptables protects users anyway even if there are no rulesets" ....
This is not untrue :) iptables does its job according to what its configured for and within those limits it protects its users...

> **scorp123 said:**
> If anyone falls for the stuff you wrote up there and anything bad happens to them afterwards it will be your fault.
That's not an argument ;) that's desperation ;

> **scorp123 said:**
> Someone should report this thread to the admins here, let's see what they think about your "abstract thinking" and giving people a false sense of security for the wrong reasons?
Why don't you do it?

> **scorp123 said:**
> In any case I am stopping here and "good luck" to anyone blindly believing what you and OP wrote up there.
S/he who believes blindly is lost anyway... no matter what you do ;)

---

### Post by Zralou on 2008-04-14
First off, this was written for windows users, the fine print of what a certain program acually does or doesn't do, is irrelevent.

Based on the windows user understanding, a firewall in windows will ask the user if they wish to allow a service/program to pass through, most times the information given about the service/program asking for permission is not a simple name or discription, but rather the actual .exe or .dll and its related location directory.  Most windows users will just click yes without understanding or knowing whether the service/program is malicious or safe.

Therefore, basaed on the above mindset, a program that does nothing when a service/program wants access, is actually doing something to protect the user from themselves.

Sara Lou

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
> It is configured - to do nothing... but still is ;) Nope. I see from your profile that you claim to be a lawyer or something. No miracle you're so fond of twisting stuff around. Well I am a UNIX administrator, and if something isn't configured then this isn't the same as "configured to do nothing". There is a big difference between the two. And if something isn't configured it isn't configured, and not "it is configured anyway even if it isn't". That may make sense for a lawyer, but from the IT administrator POV this is utter nonsense.

Sodele, und jetz hör uf stürme, ja? Et si tu es Romands: bonsoir.

---

### Post by scorp123 on 2008-04-14
> **Zralou said:**
>  a program that does nothing when a service/program wants access, is actually doing something to protect the user from themselves.  How can a program that does absolutely nothing whatsoever in its default configuration do "something to protect the user from themselves". ??

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> Nope. I see from your profile that you claim to be a lawyer or something. No miracle you're so fond of twisting stuff around. Well I am a UNIX administrator, and if something isn't configured then this isn't the same as "configured to do nothing". There is a big difference between the two. And if something isn't configured it isn't configured, and not "it is configured anyway even if it isn't". That may make sense for a lawyer, but from the IT administrator POV this is utter nonsense.

Sodele, und jetz hör uf stürme, ja? Et si tu es Romands: bonsoir.

You just can't stop sliding on a personal level, right? That doesn't help your credibility... and even being  UNIX administrator doesn't make your statements right... besides, you know nothing about my past ;)

How would you configure iptables to do nothing? Either you will set it to allow everything or you will set it to not have any rules at all... in both cases iptables is doing what it's told to do ;) hence it is configured to do nothing...

But please, elaborate the difference between "not configured" and "configured to do nothing".

> **scorp123 said:**
> Sodele, und jetz hör uf stürme, ja? Et si tu es Romands: bonsoir.
Besides, this is an englsih speaking forum and just mentioning only the two larger native populations is also... questionable.. ;)

---

### Post by Zralou on 2008-04-14
> **scorp123 said:**
> How can a program that does absolutely nothing whatsoever in its default configuration do "something to protect the user from themselves". ??

Instead of just taking snipets of a comment and twisting the words to create an argument is futile.
Quote the whole sentence and put into context the statement.  Or maybe I should break in down into "simple" terms that you can understand:

==If a program that does something can harm a system, then a program that does nothing in the same senario will protect the system, i.e. windows firewall asks if it can allow a malicious program to pass through, the user says yes (because they don't understand the conseqence), that system is then vunerable, however, if a malicious program wants to pass through, but the user knows nothing about it (because they haven't been asked to let it pass through) then the program can't compromise the system.==

Sara Lou

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  You just can't stop sliding on a personal level, right?  I was wondering who TF you are and if I should put you on my ignore list or not. You really started to annoy me for a short moment. So I browsed through your profile, through your other postings in other threads and all that. You seem to be such a nice guy ... except here where you really twist stuff around so much that it hurts.

> **hyper_ch said:**
>  ... and even being  UNIX administrator doesn't make your statements right...  And how so?

> **hyper_ch said:**
>  How would you configure iptables to do nothing?  You define rules which allow any traffic through, in any direction. That would be "configured to do nothing". And those rules would be visible in "iptables -L".

> **hyper_ch said:**
>  ... in both cases iptables is doing what it's told to do ;) Nope. Your logic is flawed. If you don't tell it anything it simply has not been told what to do. There is a difference between "not telling what to do" and "telling to do nothing" even if the end result may look the same to you.

> **hyper_ch said:**
>  But please, elaborate the difference between "not configured" and "configured to do nothing".  "Not configured": No config and no ruleset present, as is the case with Ubuntu "out of the box". 

"Configured to do nothing:" Somebody defined rulesets that are active (and visible via "iptables -L" !) to allow traffic in any directions through the firewall. Here in this scenario "configured to do nothing" would at least mean several things: Somebody did configure something here and the relevant IP filtering modules are indeed loaded and active. And depending how far "configured to do nothing" goes it could be that you at least get log messages of the network connections that the firewall let through even though the firewall does not interfere with the traffic itself. 

So for me this is a difference. Even quite an important one. 

> **hyper_ch said:**
>  Besides, this is an englsih speaking forum and just mentioning only the two larger native populations is also... questionable.. ;)  Well, just tried to be nice ... and besides I don't really speak Italian and and I definitely don't speak Raeto-Romansh ... 

In any case this here definitely is my last posting here in this thread. Tschüss, au revoir, arividerci, adio .... or whatever they say in that corner of the CH.

---

### Post by scorp123 on 2008-04-14
> **Zralou said:**
>  ==If a program that does something can harm a system, then a program that does nothing in the same senario will protect the system, i.e. windows firewall asks if it can allow a malicious program to pass through, the user says yes (because they don't understand the conseqence), that system is then vunerable, however, if a malicious program wants to pass through, but the user knows nothing about it (because they haven't been asked to let it pass through) then the program can't compromise the system.==  Slight violation to my statement above, I feel I have to answer that one:

I will break it down in simple terms to you as well. Ubuntu's firewall does nothing like this "out of the box". It does not stop anything, it does not protect you one little bit. Imagine you installed a network program such as e.g. OpenSSH and someone is now starting an attack on you. Because there is nothing configured in Ubuntu's firewall the attack will reach your system and you will not be notified in any way and with some luck and talent  on behalf of the attacker the attack will succeed and your system will be harmed. Ubuntu's firewall will "out of the box" do nothing whatsoever to prevent that from happening. Believing that you are "safe" because the firewall functionality is already built-in is wrong ... Yes, the firewall is there. But you have to configure it because otherwise you will not benefit from it.

The reason why Ubuntu is nontheless safe "out of the box" is that per default and usually there are no networked programs listening for incoming connections. The fact that the firewall isn't really active is therefore irrelevant, there is nothing a hacker could attack. But as I wrote before: this changes immediately if you e.g. install OpenSSH, Samba, telnet, FTP, Apache, or any such program.

Clear what I mean now?

---

### Post by hyper_ch on 2008-04-14
> **scorp123 said:**
> I was wondering who TF you are and if I should put you on my ignore list or not. You really started to annoy me for a short moment. So I browsed through your profile, through your other postings in other threads and all that. You seem to be such a nice guy ... except here where you really twist stuff around so much that it hurts.
No, you say I'm twisting stuff and that is a personal level... you don't argue like that as it makes you not credible.

> **scorp123 said:**
> And how so?
By just saying you're an UNIX admin you do exactely the thing you critizie the OP with ;) you will give the impression that you are (sort of) all-knowing... the same way the OP said that "you are secure". However it does not give any relevant information to this piece of problem. By referring to you as general being an UNIX admin you lead to make people believe that you actually know everything about this issue - and that is not the case...

> **scorp123 said:**
> You define rules which allow any traffic through, in any direction. That would be "configured to do nothing". And those rules would be visible in "iptables -L".
I can either define rules that allow traffic without hindrance or I can just delete all rules. I will achieve the same thing and "configure" it to my wishes... in both cases it's configured.

> **scorp123 said:**
> Nope. Your logic is flawed. If you don't tell it anything it simply has not been told what to do. There is a difference between "not telling what to do" and "telling to do nothing" even if the end result may look the same to you.
You chose not to do anything and hence you do something --> leaving it in the state it is... that's also to be configured...

> **scorp123 said:**
> "Not configured": No config and no ruleset present, as is the case with Ubuntu "out of the box".
A default installation of apache comes with some config file... is it now configured or not?

> **scorp123 said:**
> "Configured to do nothing:" Somebody defined rulesets that are active (and visible via "iptables -L" !) to allow traffic in any directions through the firewall. Here in this scenario "configured to do nothing" would at least mean several things: Somebody did configure something here and the relevant IP filtering modules are indeed loaded and active. And depending how far "configured to do nothing" goes it could be that you at least get log messages of the network connections that the firewall let through even though the firewall does not interfere with the traffic itself.
And if it was delievered with a few rules and then you delete everything? Would that still be unconfigured?

> **scorp123 said:**
> So for me this is a difference. Even quite an important one.
There is a difference, but it has nothing to do with what is contained in the config files ;)

---

### Post by scorp123 on 2008-04-14
> **hyper_ch said:**
>  A default installation of apache comes with some config file... is it now configured or not?  That's a default configuration that at least does *something*. It serves the default pages Apache usually ships with. So yes, this is "configured". A default configuration. "Configured to do nothing" would probably mean that the httpd process is listening on port 80 and accepting connections but no pages are being served (e.g. maybe DocumentRoot wasn't set properly?), which would mean you'd get a 404 and similar errors ... So here this would be a misconfiguration. Serving a blank empty page isn't "configured to do nothing", it's "serving a blank page", so again a difference. Happy with this answer?

> **hyper_ch said:**
>  And if it was delievered with a few rules and then you delete everything? Would that still be unconfigured?  Not "still" unconfigured but rather "again unconfigured". Some UNIX OS's such as Solaris have a "unconfigure" command (Solaris: "sys-unconfig") so the term is quite common. If you deleted all iptable rules then saying something like "I unconfigured the firewall" when you e.g. informed the rest of the team would be appropriate and everybody would understand what you mean.

So, now I am really gone from this thread.

---

### Post by brian_p on 2008-04-14
> **hyper_ch said:**
> So the statements are correct and with the default configuration users are protected.

At the very least the statements regarding firewalls are confusing and contradictory. The safeness of a default configuration has nothing to do with iptables. A kernel compiled without it would not imperil the system.

---

### Post by Zralou on 2008-04-14
> **scorp123 said:**
> Slight violation to my statement above, I feel I have to answer that one:

I will break it down in simple terms to you as well. Ubuntu's firewall does nothing like this "out of the box". It does not stop anything, it does not protect you one little bit.
And by the same token, it does not allow anything either, so you can't allow malicious programs to pass-through, therefore keeping the system safe.
> **scorp123 said:**
> 
 Imagine you installed a network program such as e.g. OpenSSH and someone is now starting an attack on you.
That is irrelevent, that is now adding other criteria into the equation, we're talking about a standard 'OOTB' install of Linux by a windows user, not a UNIX admin.  If someone has the knowhow to install programs that you list, then they would hopefully have the knowhow to configure the firewall to match.

> **scorp123 said:**
> 
The reason why Ubuntu is nontheless safe "out of the box" is that per default and usually there are no networked programs listening for incoming connections. The fact that the firewall isn't really active is therefore irrelevant, there is nothing a hacker could attack. But as I wrote before: this changes immediately if you e.g. install OpenSSH, Samba, telnet, FTP, Apache, or any such program.

Clear what I mean now?

As stated above, most of your comments are based around "extra" additions to the basic install, which does affect the functionallity of the firewall, no one disputes that.  But we are talking about the effect of a basic install without modification, and how secure the system is in that particular state.  Any modification to that senario will have an impact of the outcome.

Is that clear what I mean now?

Sara Lou

---

### Post by brian_p on 2008-04-14
> **Zralou said:**
> 

 > Originally Posted by scorp123  
I will break it down in simple terms to you as well. Ubuntu's firewall does nothing like this "out of the box". It does not stop anything, it does not protect you one little bit.


And by the same token, it does not allow anything either, so you can't allow malicious programs to pass-through, therefore keeping the system safe.

With no filter rules defined iptables allows all packets in and out. Having no filter rules is the default. In the light of this your assertion fails under even the mildest of scrutiny.

> That is irrelevent, that is now adding other criteria into the equation, we're talking about a standard 'OOTB' install of Linux by a windows user, not a UNIX admin.  If someone has the knowhow to install programs that you list, then they would hopefully have the knowhow to configure the firewall to match.

scorp123 was trying to be helpful by contrasting the default situation with one where a service is provided externally. You do not appear to understand the default situation so that is probably why you do not see its relevance.

Incidentally, a firewall is not required to configure a service safely.

> As stated above, most of your comments are based around "extra" additions to the basic install, which does affect the functionallity of the firewall, no one disputes that.  But we are talking about the effect of a basic install without modification, and how secure the system is in that particular state.  Any modification to that senario will have an impact of the outcome.

The default install is perfectly safe because no services are running so there is no external access. That's it. There is no more to it

---

### Post by Zralou on 2008-04-14
> **brian_p said:**
>  You do not appear to understand the default situation...

The default install is perfectly safe because no services are running so there is no external access. That's it. There is no more to it

Exactly what I have been saying.....  So it seems I DO, in fact, understand.

Sara Lou

---

### Post by Chame_Wizard on 2008-04-14
> **thelatinist said:**
> [*Please note: this is a first draft of an FAQ I wrote up with people migrating from Windows in mind.  In my experience, such people very often ask the same few questions about basic maintenance over and over again.  If you have any corrections, suggestions, additions, etc., please post them and I will work them into the thread.*]

People migrating from windows have a special set of concerns stemming from years running an insecure and poorly-designed operating system.  This FAQ is designed to answer some of the most frequently asked questions about security and maintenance in Linux, namely:
[LIST=1]
[*]How do I install Anti-virus Software?
[*]How do I install a firewall?
[*]How do I configure the firewall? 
[*]How do I get Firestarter to run automatically at startup?
[*]How do I defragment my hard drive?
[*]What am I going to do with all the time I used to spend doing Windows maintenance?
[/LIST]

**How do I install Anti-virus Software?**

You probably do not need anti-virus software unless you want to use it to check a windows computer over a network.  There are no serious Linux viruses in the wild, and if you follow simple precautions like only downloading software from trusted sources you will not get any viruses.  Nor do you have to worry about passing on Windows viruses to your friends unless you do something foolish like forward an attachment your receive in email.  As strange as it may seem to someone coming from Windows, you don't need to install tons of software to secure your computer under Linux: Linux is secure by design.

**How do I install a Firewall?**

You do not need to install a firewall because Linux has one already built in, called iptables!  Again, adding bloated software to a fresh install just to make it secure is the old Windows model.  If you are using Ubuntu while reading this, iptables is running in the background, protecting you with a default configuration. For most people, this default will be enough.  If you need to customize the firewall's rules or close specific ports, that is easy to do.

**How do I configure the Firewall?**

In most cases you don't need to!  A default Ubuntu installation does not include any software that is listening for incoming connections.  If you have a static ip address or if you install server software on your computer, you will probably want to configure custom rules for handling incoming connections.  The easiest way to configure iptables is probably to use Firestarter, a GUI utility which is available in Applications > Add/Remove... or through your favorite package manager.  Firestarter will walk you through closing ports and provides an easy way to configure other rules.  When you are done configuring, simply close Firestarter.  Iptables will continue to run silently in the background.

**How do I get Firestarter to run automatically at startup?**

You do not need to keep Firestarter running.  Once iptables is configured, your computer will be protected.  You only need to run Firestarter again if you want to change your firewall settings (e.g., to open a port you previously closed).

**How do I defragment my hard drive?**

Again, you don't need to!  Linux uses a file system called ext3 which is much more careful about its placement of files.  Basically, it leaves room for files to grow so that they don't become fragmented.  If a file should become fragmented, the drive will naturally defragment as you save and delete files.  There just isn't a need for regular disk maintenance to keep your system running efficiently.  If you dual boot, you will have to do any defragmentation on your NTFS partitions from within Windows.

**What am I going to do with all the time I used to spend doing maintenance on my operating system?**

That's up to you, but can I suggest you spend a little of it giving back to the community at [http://www.ubuntuforums.com/](http://www.ubuntuforums.com/)?

so many questions:lolflag:

but it's good

---

### Post by scorp123 on 2008-04-14
> **Zralou said:**
>  And by the same token, it does not allow anything either  Wrong. It is not active, there is no filtering taking place, so every traffic regardless of its nature will pass through. Now clear what I mean?

> **Zralou said:**
>  so you can't allow malicious programs to pass-through, therefore keeping the system safe.  See above. ](*,)

> **Zralou said:**
>  then they would hopefully have the knowhow to configure the firewall to match.  Hopefully, yes. But browsing through the forums I often enough see newcomers playing with things such as Apache (which they of course have every right do so ... ) thinking they are safe "because there is a firewall in Ubuntu". That part is only true if you took the care and configured something or if you happen to have a hardware firewall, e.g. in your broadband router. Otherwise it's not and any network packet will be allowed to pass through.

> **Zralou said:**
>  But we are talking about the effect of a basic install without modification, and how secure the system is in that particular state. I wrote about that already. This has ***nothing*** to do with the firewall. Hence OP's statement is still partially false. Ubuntu is safe in it's default state because there is no program installed (yet) that would accept incoming connections ... No SSH, no Apache, no Samba, nothing like that. So a wannabe hacker has nothing to attack, there simply would be no program that would respond to the incoming packets. But this has absolutely nothing to do with the firewall. I already wrote that several times now.

---

### Post by scorp123 on 2008-04-14
> **brian_p said:**
> With no filter rules defined iptables allows all packets in and out. Having no filter rules is the default. In the light of this your assertion fails under even the mildest of scrutiny. 

scorp123 was trying to be helpful by contrasting the default situation with one where a service is provided externally. You do not appear to understand the default situation so that is probably why you do not see its relevance.  Thank God at least one human being here who really understands what I write! =D>

---

### Post by koenn on 2008-04-14
> **Zralou said:**
> Exactly what I have been saying.....  So it seems I DO, in fact, understand.

Sara Lou

you seem to have missed one detail though :

- the default configuration of iptables on Ubuntu is to allow every connection to, from, and through the computer in question
- the op claims that "iptables is running in the background, protecting you with a default configuration."

I don't want to argue whether or not "allow all connections" means the same as "protecting you"

A lot of people, especially newbies, are impressed by the abundance of available software and the possibility of such cool stuff as remote logins or running your own website (al for free !) on a PC or a laptop, so they **will** install openssh-server, apache, bind, or samba shares and vnc open to the internet ...
What's more, they'll expect to be secured by the "iptables quietly running in the background, protecting you". And then their computer gets  cracked, compromized, rooted, owned, you name it.

so, claiming that  iptables is running in the background, protecting you with a default configuration is
1/ incorrect (as in : the statement is not true)
2/ wrong (as in misleading and can lead to rather bad consequences)

what *is* protecting you on a default ubuntu is the absence of services / daemons that one can  connect to from remote.

---

### Post by mips on 2008-04-14
A simple and easy way to configure iptables would be to use [Firewall Builder]("http://www.fwbuilder.org/")

---

### Post by aysiu on 2008-04-14
Forgive me in advance for tooting my own horn, but I'd much rather refer people to the Psychocats page on security:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

1. I advise people not to change network settings unless they know what they're doing
2. jdong does a great guest-writing of the two paragraphs on iptables and I think explains it rather well
3. The URL is much easier to remember than the *showthread.php?t=640752* at the tailend of this thread.
4. I link to a far lengthier and more in-depth explanation of security

---

### Post by scorp123 on 2008-04-14
> **koenn said:**
> - the default configuration of iptables on Ubuntu is to allow every connection to, from, and through the computer in question
- the op claims that "iptables is running in the background, protecting you with a default configuration."

I don't want to argue whether or not "allow all connections" means the same as "protecting you" ...

A lot of people, especially newbies, are impressed by the abundance of available software and the possibility of such cool stuff as remote logins or running your own website (al for free !) on a PC or a laptop, so they **will** install openssh-server, apache, bind, or samba shares and vnc open to the internet ...
What's more, they'll expect to be secured by the "iptables quietly running in the background, protecting you". And then their computer gets  cracked, compromized, rooted, owned, you name it.

so, claiming that  iptables is running in the background, protecting you with a default configuration is
1/ incorrect (as in : the statement is not true)
2/ wrong (as in misleading and can lead to rather bad consequences) 

what *is* protecting you on a default ubuntu is the absence of services / daemons that one can  connect to from remote. My point exactly and what I have been trying to get through here in over a dozen postings here. ](*,) Thank you. =D>

---

### Post by koenn on 2008-04-14
> **scorp123 said:**
> My point exactly and what I have been trying to get through here in over a dozen postings here. ](*,) Thank you. =D> you're welcome

---

### Post by ice60 on 2008-04-14
i think maybe the most commonly used security program is rkhunter for helping find rootkits, i run that sometimes. 

ubuntu comes with apparmor enabled (i think??) i use apparmor and have configured aide too. but, i know i'm odd when it comes to security and no one really cares about it! have a look for threads about apparmor and how to use it, i never managed to find one clear guide on how to set it up and just worked it out myself lol.

---

### Post by saxuntu on 2008-04-14
I thought i read somewhere that iptables is configured to allow inbound and outbound. Firestarter is need to close the inbound. If there's any truth to this it need's to be accounted for.

---

### Post by scorp123 on 2008-04-15
> **ice60 said:**
>  ubuntu comes with apparmor enabled (i think??)  7.04 doesn't .... 7.10 and the upcoming 8.04 do. Details can be found here:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by ice60 on 2008-04-15
> **scorp123 said:**
> 7.04 doesn't .... 7.10 and the upcoming 8.04 do. Details can be found here:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

thanks.

i really, really wish we could get a good thread going about how to use it properly. using it isn't too difficult, but an apparmor thread with good default profiles in would be great. if you can profile all your network facing programs it's a big step to staying secure.

---

### Post by Tundro Walker on 2008-04-15
> "What am I going to do with the time I save?"

I tell you, that was the hardest part in transitioning to Linux for me.  Suddenly all this time I spent baby-sitting my Windows comp, defragging, deleting old files, running anti-virus, looking for ways to squeeze out more performance ... it was freed up, and I was going stir-crazy with the extra time on my hands. :)

---

