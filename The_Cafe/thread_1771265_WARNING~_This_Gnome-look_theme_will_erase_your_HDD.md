---
title: "WARNING~ This Gnome-look theme will erase your HDD"
date: 2011-05-30
forum: The Cafe
---

### Post by Rasa1111 on 2011-05-30
Just a friendly warning to anyone who visits gnome-look. 
[COLOR=Red]INSTALLING THIS WILL DELETE YOUR HDD[/COLOR]~ [http://gnome-look.org/content/show.php/Appows+%28gives+new+life+to+yur+Ubuntu%29?content=142208](http://gnome-look.org/content/show.php/Appows+%28gives+new+life+to+yur+Ubuntu%29?content=142208)
[SIZE=3][B]
So do not use it. [/B][/SIZE]

One of the very few times I installed something from there without looking at the comments first..
and it wiped my entire 11.04-Natty partition. 

My 10.10 partition is intact, but it completely destroyed my 11.04 side. 

So,
 This just goes to show that even if your are usually quite vigilante.. 
You can still slip up and screw yourself. 
Like i just did. 

Be careful. 
Out there be *scumbag* monsters... :???:

---

### Post by s.fox on 2011-05-30
Have you reported the submission?

---

### Post by Rasa1111 on 2011-05-30
Yes i have.

---

### Post by Noz3001 on 2011-05-30
Silly little kids. Does Ubuntu not have some kind of protection from rm -rf / yet?

---

### Post by Rasa1111 on 2011-05-30
> **Noz3001 said:**
> Silly little kids. Does Ubuntu not have some kind of protection from rm -rf / yet?

none other than "common sense" I guess..
Which I am apparently sorely lacking in today. :o

---

### Post by BrokenKingpin on 2011-05-30
I will never understand why people do this. I have pretty much stopped using the *-Look websites for this crap (sometimes I will try one in a VM first). They should implement a review system before stuff is published, but I am not sure they have the admin staff for it.

---

### Post by tjwoosta on 2011-05-30
> Silly little kids. Does Ubuntu not have some kind of protection from rm -rf / yet?

> none other than "common sense" I guess..
Which I am apparently sorely lacking in today. :o


```

tj@tj-ubuntu:~$ sudo rm -rf /
[sudo] password for tj: 
rm: it is dangerous to operate recursively on `/'
rm: use --no-preserve-root to override this failsafe
tj@tj-ubuntu:~$

```

---

### Post by PhillyPhil on 2011-05-30
Rasa, google his user name.  It gives his real name and twitter account as the first hit.

---

### Post by Rasa1111 on 2011-05-30
> **tjwoosta said:**
> ```

tj@tj-ubuntu:~$ sudo rm -rf /
[sudo] password for tj: 
rm: it is dangerous to operate recursively on `/'
rm: use --no-preserve-root to override this failsafe
tj@tj-ubuntu:~$

```

yup

---

### Post by neu5eeCh on 2011-05-30
So how did it work. I'm almost tempted to download it and run it in VM. 

Was there anything that should have tipped you off before installing it? - just so the rest of us don't make the same mistake...

---

### Post by tjwoosta on 2011-05-30
Probably should have tipped somebody off that a gtk2 theme was packaged as a .deb

Should have been tar so people on other distros can install.

---

### Post by BrokenKingpin on 2011-05-30
> **Noz3001 said:**
> Silly little kids. Does Ubuntu not have some kind of protection from rm -rf / yet?
Well, the correct system is in place to protect against this, as you need root access to install a package. The killer here is that it is all to easy to assume that a site like this has legit content.

---

### Post by Rasa1111 on 2011-05-30
> **VTPoet said:**
> So how did it work. I'm almost tempted to download it and run it in VM. 

Was there anything that should have tipped you off before installing it? - just so the rest of us don't make the same mistake...

 Only the same thing one often gets when installing something in 11.04 via software center..
*"package is of bad quality~ install anyway?"*

This same "warning" happens often when installing things in 11.04. 

The real "tip off" would have been to read the frickin' comments first. 
Which I usually do, BUT, not today. Go figure. lol

Guess i chalk it up to a lesson... 
"Stay vigilante or get bent" 
 gahh
:rolleyes:

---

### Post by 3Miro on 2011-05-30
I am tempted to try this under VirtualBox, the rm command shouldn't work even if it is under the postinst of the .deb file.

A word of caution: NEVER INSTALL THEMES FROM DOWNLOADED .DEB FILES! THIS COUNTS DOUBLE FOR AUTOMATED SCRIPTS! I only install things if I see a bunch of art files (pictures and icons).

The real test here is to find out how long it will take the Gnome-looks.org guys to remove this piece of garbage, close the account and depending on where the poster is, they can report to authorities.

---

### Post by Rasa1111 on 2011-05-30
> **tjwoosta said:**
> Probably should have tipped somebody off that a gtk2 theme was packaged as a .deb

Should have been tar so people on other distros can install.

 Yeah but there are quite a few themes today that are packaged as .deb,
So I thought nothing of it. :???:

> The real test here is to find out how long it will take the  Gnome-looks.org guys to remove this piece of garbage, close the account  and depending on where the poster is, they can report to authorities.

agreed.

---

### Post by Irihapeti on 2011-05-30
I only hope this wakes the gnome-look admins up to the need to check packages before they're offered to the public.

---

### Post by CharlesA on 2011-05-30
Another one of those "theme as a deb" deals?

---

### Post by 3Miro on 2011-05-30
> **Irihapeti said:**
> I only hope this wakes the gnome-look admins up to the need to check packages before they're offered to the public.

+1. This is not the first time something like this has happened. Gnome-looks should accept tar files with art, but they should check/verify .deb .rpm or shell scripts.

---

### Post by 3Miro on 2011-05-30
> **CharlesA said:**
> Another one of those "theme as a deb" deals?

Yes, it is an rm command in postinst.

---

### Post by CharlesA on 2011-05-30
> **3Miro said:**
> +1. This is not the first time something like this has happened. Gnome-looks should accept tar files with art, but they should check/verify .deb .rpm or shell scripts.

This has happened once before (that I know of at least), huge +1 for that.

> **3Miro said:**
> Yes, it is an rm command in postinst.

Thanks.

---

### Post by BigSilly on 2011-05-30
I see it in postinst. What a complete ar**hole. Hope the Gnome-Look people remove this soon.

Thing is, a lot of theme packages there do come as .deb files, so I know exactly what the OP is referring to. You don't expect the site to be hosting anything nasty, but sadly malicious people are out there. :(

Though it's rotten for those affected, I'd just like to say thank you for the heads up. I'm not running a Debian based system at the moment, but regardless it's certainly given me a sufficient poke in the head to keep my eyes on what I download and install.

---

### Post by Rasa1111 on 2011-05-30
> **BigSilly said:**
> I see it in postinst. What a complete ar**hole. Hope the Gnome-Look people remove this soon.

_*Thing is, a lot of theme packages there do come as .deb files, so I know exactly what the OP is referring to*_. You don't expect the site to be hosting anything nasty, but sadly malicious people are out there. :(

Though it's rotten for those affected, I'd just like to say thank you for the heads up. I'm not running a Debian based system at the moment, but regardless it's certainly given me a sufficient poke in the head to keep my eyes on what I download and install.

 No problem, and thank you. <3

---

### Post by Aquix on 2011-05-30
Glad he didn't completely destroyed your system at least. Have some :popcorn:

Yeah. I don't like deb's from third party sites. I don't even likes scripts I'm not able to check first, or commands for that matter. It's one of the things that comes with using a powerful os, splitting atoms for bombs or electricity kind of thing.

---

### Post by 3Miro on 2011-05-30
> **BigSilly said:**
> 
Though it's rotten for those affected, I'd just like to say thank you for the heads up. I'm not running a Debian based system at the moment, but regardless it's certainly given me a sufficient poke in the head to keep my eyes on what I download and install.

Some of the themes come with install scripts, not .deb/rpm packages. The install scripts are just as dangerous.

BTW, I just rested the damned thing under VirtualBox with Maveric and it does work.

---

### Post by lucazade on 2011-05-30
I'm speechless... mother of idiots is always pregnant.

---

### Post by Hwæt on 2011-05-30
> **3Miro said:**
> +1. This is not the first time something like this has happened. Gnome-looks should accept tar files with art, but they should check/verify .deb .rpm or shell scripts.

They shouldn't accept .deb, .rpm, or shell scripts **at all**. There is hardly a necessity for them. If your theme really requires a deb, then maybe you should reconsider how your theme is implemented.

---

### Post by Irihapeti on 2011-05-30
I just downloaded it out of curiosity and unarchived it to have a look.

No need to run it, even though I have a spare install on a USB drive I could use - I trust that I understand what the command does.:twisted:

I note that there's someone's email address in the control file. Does it belong to the submitter, or is it yet another trick to try and get other people into trouble?

If so, I won't say what I think....

---

### Post by Rasa1111 on 2011-05-30
> **Aquix said:**
> Glad he didn't completely destroyed your system at least. Have some :popcorn:

Yeah. I don't like deb's from third party sites. I don't even likes scripts I'm not able to check first, or commands for that matter. It's one of the things that comes with using a powerful os, splitting atoms for bombs or electricity kind of thing.


lol, thanks. :P
you're right.

> BTW, I just rested the damned thing under VirtualBox with Maveric and it does work. 	

lol, it sure does. :o

> I just downloaded it out of curiosity and unarchived it to have a look.

No need to run it, even though I have a spare install on a USB drive I  could use - I trust that I understand what the command does.:twisted:

I note that there's someone's email address in the control file. Does it  belong to the submitter, or is it yet another trick to try and get  other people into trouble?

If so, I won't say what I think.... 	

well...
I'd like to know what you think...
I will gladly accept a PM. lol :P

---

### Post by Zero2Nine on 2011-05-30
That sucks, thanks for warning us! A reminder to us all to be careful.

---

### Post by Irihapeti on 2011-05-30
> **PhillyPhil said:**
> Rasa, google his user name.  It gives his real name and twitter account as the first hit.

That's not the name that's in the control file. Either he's using more than one name on the net, or he wants someone else to get the flak.

No, Rasa, I won't tell you what I think - I'd get chucked off the forums...

---

### Post by Markmental on 2011-05-30
i would be suspicious of a .deb

---

### Post by Rasa1111 on 2011-05-30
> **Irihapeti said:**
> That's not the name that's in the control file. Either he's using more than one name on the net, or he wants someone else to get the flak.

No, Rasa, I won't tell you what I think - I'd get chucked off the forums...


Ok, I don't want you getting chucked. 

I think he is trying to get someone else in trouble.. or "get the flak"..
as the name and email in the file lead me to someone who already has a history within the linux community. 
and i just can't see someone putting their own info into a file like that. 

but damn..
now you've got me curious.. :???:

---

### Post by Random_Dude on 2011-05-30
Thanks for the heads-up Rasa, I didn't know that there were themes packet as .deb files. Your can never be too careful, even when running Linux.
That account was created 5 hours ago, probably just for this purpose. Shutting it down won't do much, another guy will popup.

Gnome-Look should really check the code in the submissions before accepting.

---

### Post by Irihapeti on 2011-05-30
What about putting a warning in our sigs? Or should there be another sticky along the lines of "malicious commands"?

---

### Post by 3Miro on 2011-05-30
> **Rasa1111 said:**
> content is finally removed from gnome-look.

Pretty fast, although not as fast as Ubutnuforums.

---

### Post by Hwæt on 2011-05-30
The *-look sites all seem to be down now. I can't connect to them.

---

### Post by Irihapeti on 2011-05-30
I know of a guy who does stuff like that. He's spent years p*****g off his neighbours.

Only thing is, he's had something like seven heart attacks and he's not even 40 yet.

Things have a way of catching up with you.

---

### Post by Irihapeti on 2011-05-30
> **Hwæt said:**
> The *-look sites all seem to be down now. I can't connect to them.

If they haven't got the staff to check all submissions, they should stay down permanently.

---

### Post by Rasa1111 on 2011-05-30
> **Irihapeti said:**
> I know of a guy who does stuff like that. He's spent years p*****g off his neighbours.

Only thing is, he's had something like seven heart attacks and he's not even 40 yet.

Things have a way of catching up with you.

Absolutely. 
Sad, sad little people. 


> If they haven't got the staff to check all submissions, they should stay down permanently. 	

Couldn't agree more.

---

### Post by Random_Dude on 2011-05-30
> **Hwæt said:**
> The *-look sites all seem to be down now. I can't connect to them.

Really?
I've just connected to gnome-look. :confused:

---

### Post by ivanovnegro on 2011-05-30
Thank you Rasa for this great info, not that I ever use the Gnome Look org site for themes, I found it always too suspicious.
Great, they removed it now. I think you saved maybe some people's systems . :D

---

### Post by Rasa1111 on 2011-05-30
> **Random_Dude said:**
> Really?
I've just connected to gnome-look. :confused:

 Me to.

---

### Post by Rasa1111 on 2011-05-30
> **ivanovnegro said:**
> Thank you Rasa for this great info, not that I ever use the Gnome Look org site for themes, I found it always too suspicious.
Great, they removed it now. I think you saved maybe some people's systems . :D

 No problem man. 
Hope so. <3

---

### Post by Hwæt on 2011-05-30
Not everything on the *-look sites is bad. Even if they don't have the staff to check all submissions, these sites are an invaluable resource for people who legitimately want to share art that they believe improves the UI of some Window Managers and DEs.

That being said, it's still always good to use discretion when downloading something from the site, as something could be dangerous.

---

### Post by Irihapeti on 2011-05-30
> **Hwæt said:**
> Not everything on the *-look sites is bad. Even if they don't have the staff to check all submissions, these sites are an invaluable resource for people who legitimately want to share art that they believe improves the UI of some Window Managers and DEs.

That being said, it's still always good to use discretion when downloading something from the site, as something could be dangerous.

What you say is true. However, what are the new users supposed to do who don't know how to evaluate these things?

When I was a newbie, I wouldn't have had a clue what to look for.

That's why I'm being hard-line about it.

---

### Post by Hwæt on 2011-05-30
> **Irihapeti said:**
> What you say is true. However, what are the new users supposed to do who don't know how to evaluate these things?

When I was a newbie, I wouldn't have had a clue what to look for.

That's why I'm being hard-line about it.

Thank you for agreeing. You have a point, but it's just more motivation for educating people on this subject. It's what you'd do in the real world for any disease. I mean, I know it'd be bad for business, but the *-look sites would be better off with a banner on the top offering some sort of warning for new users.

---

### Post by Dry Lips on 2011-05-30
I think gnome-look is a great site, too bad things like this happen.
Guess this is kind of a wake-up call to be more suspicious when
it comes to downloading stuff that's not in the repos.

---

### Post by CraigPaleo on 2011-05-30
I'm driving myself crazy trying to figure out how this makes any sense at all. I guess this is the type of person who goes home and kicks his dog because he's mad at his boss. 

I don't want to give him any ideas but this is eerily reminiscent of something even more sinister.

---

### Post by Barrucadu on 2011-05-30
Am I the only person who would look at that and think "A .deb file for a theme? I think I'll extract it first and have a look."? It falls under the same category of common sense as "don't give arbitrary programs your password".

---

### Post by BrokenKingpin on 2011-05-30
Packing themes as .Deb files is perfectly fine, as it makes it very easy to get the theme installed correctly. Just ensure you are downloading them from a trusted source, and maybe crack it open before installing it.

Same goes with applications, having them in a .Deb makes it way easier to install, but you still have to trust the the place you got it from.

So it really isn't how the site distributes the themes that is causing the issues, it is the regulations in place to prevent malicious packages and scripts in the first place.

---

### Post by 3Miro on 2011-05-30
> **BrokenKingpin said:**
> Packing themes as .Deb files is perfectly fine, as it makes it very easy to get the theme installed correctly. Just ensure you are downloading them from a trusted source, and maybe crack it open before installing it.

Same goes with applications, having them in a .Deb makes it way easier to install, but you still have to trust the the place you got it from.

So it really isn't how the site distributes the themes that is causing the issues, it is the regulations in place to prevent malicious packages and scripts in the first place.

So Gnome-looks should not be considered a "trusted" site. They should put a large disclaimer when downloading the files: "Gnome-looks doesn't check the files and they are sole responsibility for the people that posted them." Otherwise it looks very legitimate.

The issue is caused by the way the themes are distributed. A problem like that wouldn't happen with a .tar file. .debs are executed with root privileged, .tar only put files in .themes.

If Gnome-looks cannot check all the .deb or all the scripts, then they should either not accept such files or put a large warning (do it at your own risk).

---

### Post by CraigPaleo on 2011-05-30
Does anyone know if that can happen if you download your themes through KDE's system settings?

---

### Post by 3Miro on 2011-05-30
> **CraigPaleo said:**
> Does anyone know if that can happen if you download your themes through KDE's system settings?

KDE System Settings doesn't run as root, so any potential damage is contained to the account that you are using (which is still potentially a lot of damage).

The question would be if KDE allows for custom scripts or is it  just downloading a bunch of art files (my guess is the latter, but I am not 100% sure). The .deb system installs files in specific folders and then runs scripts to make sure all settings are correct. The bad code was part of the script.

---

### Post by CraigPaleo on 2011-05-30
> **3Miro said:**
> KDE System Settings doesn't run as root, so any potential damage is contained to the account that you are using (which is still potentially a lot of damage).

The question would be if KDE allows for custom scripts or is it  just downloading a bunch of art files (my guess is the latter, but I am not 100% sure). The .deb system installs files in specific folders and then runs scripts to make sure all settings are correct. The bad code was part of the script.

Thanks. There have been some themes I've downloaded that didn't appear to do anything. If those were scripts instead of art, it may explain it. I would think someone would have thought of it before. I hope so anyway.

---

### Post by odiseo77 on 2011-05-30
Thanks for the heads up; luckily, the content seems to be removed by now (I can't find it when I click on the link). Another reason to remember people must be very careful with the stuff they download/install from 3rd party sites :frown:

---

### Post by grahammechanical on 2011-05-30
Give me a set of good quality themes, backgrounds, icons and that kind of stuff as part of the distribution and I would be happy to use a version of Ubuntu that severely limits my freedom to modify the desktop. It would protect my system from something like this, would it not?

I liked the improvements in backgrounds that came with 10.10 and the ability to cycle through the backgrounds. Things have moved further in this direction in 11.04. If Ubuntu has style and design would you be tempted to look elsewhere?

Some see the Unity UI as being restrictive. Perhaps it should be seen as step towards securing the OS from attacks like this and from user self inflicted wounds.

Regards.

---

### Post by Macskeeball on 2011-05-30
> **Rasa1111 said:**
> vigilante

You keep using [that word](http://www.merriam-webster.com/dictionary/vigilante). I do not think it means [what you think it means](http://www.merriam-webster.com/dictionary/vigilant).

---

### Post by nerdopolis on 2011-05-30
> **CraigPaleo said:**
> Does anyone know if that can happen if you download your themes through KDE's system settings?

Well... I think Plasmoids have access to every file you do (look at the folder view plasmoid). While a rouge one could not wipe out /usr or /etc, it could mess with /home/username...

---

### Post by VCoolio on 2011-05-30
> **grahammechanical said:**
> [...]
Some see the Unity UI as being restrictive. Perhaps it should be seen as step towards securing the OS from attacks like this and from user self inflicted wounds.

Regards.

This is a case of not to be trusted third party software and hasn't much to do with being able to configure stuff. Just look at all the hate posts about "the ugly default orange theme" and "where do I configure this" and "howto change stuff in unity" going all the way from gtk2 to gdm to grub to splash to prompts and whatever. It's what people like in linux: you can change anything to your needs. If you're a bit of an autodidact you can setup your own gtk theme in a day. You're going to p*ss off(1) a lot of people if you restrict ways to configure stuff. The opportunity to configure and the ways you get the stuff to configure with are to be kept separate.
Use common sense, put all theme stuff in ~/.themes (who needs it all in the system directories anyway?) or use themes from the repositories, there are enough there.
It's good to be warned again though. I always install everything I fancy as I have yet to be punished for it. Stupid. But I hardly ever install .debs (I use either repos or source code, I want to be up to date), maybe that's my luck.

1 Is this such bad language that it's censored? I'm not a native English speaker, so apologies for offending anyone.

---

### Post by Rasa1111 on 2011-05-30
> **Macskeeball said:**
> You keep using [that word](http://www.merriam-webster.com/dictionary/vigilante). I do not think it means [what you think it means](http://www.merriam-webster.com/dictionary/vigilant).

yeah, i was spelling it wrong.

---

### Post by el_koraco on 2011-05-30
I know this kid, he was active on some threads with mindless rants. Go figure.

---

### Post by BigCityCat on 2011-05-30
It won't be long and this guy will be on TV for a rampage shooting like that weirdo in Arizona.

The great thing is if you keep your data backed up it's a free and quick reinstall.

---

### Post by Timmer1240 on 2011-05-30
Ive installed a few things from gnome look usually Im pretty careful and read the reviews but sorry to hear this happening to you.Gonna be extra cautious from now on wouldnt want to bork my system I got er how I want it!

---

### Post by 3Miro on 2011-05-30
> **Timmer1240 said:**
> Ive installed a few things from gnome look usually Im pretty careful and read the reviews but sorry to hear this happening to you.Gonna be extra cautious from now on wouldnt want to bork my system I got er how I want it!

That guy had made several bogus accounts and he had given himself good reviews.

---

### Post by CraigPaleo on 2011-05-30
> **nerdopolis said:**
> Well... I think Plasmoids have access to every file you do (look at the folder view plasmoid). While a rouge one could not wipe out /usr or /etc, it could mess with /home/username...
I only download Plasmoids from the repos. Themes I add through system settings.

---

### Post by Random_Dude on 2011-05-31
> **3Miro said:**
> That guy had made several bogus accounts and he had given himself good reviews.

You've got to be careful with this.
I think the best option would be to download themes which are older. I always go to the top rated or the most download, I'm too lazy to go fishing for some cool new themes.

Cheers :cool:

---

### Post by Aquix on 2011-05-31
The good thing is that crap like this gets shut down fast because of the community. May be a good idea to email the ubuntu blogs, they might be interested in the story, and the warning will get out there to more people.

:KS

---

### Post by NormanFLinux on 2011-05-31
Sounds like packaged commands to erase the installed OS. Not funny at all. If you want to change backgrounds, picture files are perfectly safe. NEVER install a theme or picture from a deb. or rpm. file.

In Unix computing, you need to use common sense, just like with Windows. Stay safe!

---

### Post by lucazade on 2011-05-31
> **NormanFLinux said:**
> Sounds like packaged commands to erase the installed OS. Not funny at all. If you want to change backgrounds, picture files are perfectly safe. NEVER install a theme or picture from a deb. or rpm. file.

In Unix computing, you need to use common sense, just like with Windows. Stay safe!

A correct advice would be to open the .deb file (which is a .tar.gz file) with file-roller, look into debian/postinst file (which is a text file) and see what it does. 

In this case there was a "sudo rm -rf /" which erase everything on hd.. 

The same thing could happen also with programs packaged in .deb and not only for themes or backgrounds.

---

### Post by Macskeeball on 2011-05-31
> **lucazade said:**
> In this case there was a "sudo rm -rf /" which erase everything on hd.. 

That command actually does more than that. It erases everything on any writable filesystem mounted at the time. It's not limited to the HD you're booted from.

---

### Post by Zlatan on 2011-05-31
> **Rasa1111 said:**
> Just a friendly warning to anyone who visits gnome-look. 
[COLOR=Red]INSTALLING THIS WILL DELETE YOUR HDD[/COLOR]~ [http://gnome-look.org/content/show.php/Appows+%28gives+new+life+to+yur+Ubuntu%29?content=142208](http://gnome-look.org/content/show.php/Appows+%28gives+new+life+to+yur+Ubuntu%29?content=142208)
[SIZE=3][B]
So do not use it. [/B][/SIZE]

One of the very few times I installed something from there without looking at the comments first..
and it wiped my entire 11.04-Natty partition. 

My 10.10 partition is intact, but it completely destroyed my 11.04 side. 

So,
 This just goes to show that even if your are usually quite vigilante.. 
You can still slip up and screw yourself. 
Like i just did. 

Be careful. 
Out there be *scumbag* monsters... :???:

[COLOR="DarkOrange"]**r.e.p.o.s. o.n.l.y.**[/COLOR] and you're safe

---

### Post by lucazade on 2011-05-31
> **Macskeeball said:**
> That command actually does more than that. It erases everything on any writable filesystem mounted at the time. It's not limited to the HD you're booted from.

Well spotted.. it will wipe out also writable stuff mounted in /media

---

### Post by NovaAesa on 2011-05-31
> **Zlatan said:**
> [COLOR="DarkOrange"]**r.e.p.o.s. o.n.l.y.**[/COLOR] and you're safe
Actually, this isn't really true. There's nothing at all guaranteeing that a package installed from a repo is safe. Any Job Bloggs can set up their own repo to distribute software. If anything, you can only really trust the official Ubuntu repos.

---

### Post by 3Miro on 2011-05-31
> **NovaAesa said:**
> Actually, this isn't really true. There's nothing at all guaranteeing that a package installed from a repo is safe. Any Job Bloggs can set up their own repo to distribute software. If anything, you can only really trust the official Ubuntu repos.

I think he meant the official repos. Using unofficial repos is no different then downloading a .deb file.

I think the official community repos are not anonymous. We know who puts what where, hence if someone tries to be malicious, there will be real consequences (legal ones).

---

### Post by Thewhistlingwind on 2011-05-31
> **NovaAesa said:**
> Actually, this isn't really true. There's nothing at all guaranteeing that a package installed from a repo is safe. Any Job Bloggs can set up their own repo to distribute software. If anything, you can only really trust the official Ubuntu repos.

Of course, because Linux users have virtually (And in actuality) no restrictions on their install CD's, they have an option open to them thats usually closed for windows users because of product keys and the like:

Virtualbox

---

### Post by samigina on 2011-05-31
Thats why ppas doesnt look so good for me...

---

### Post by Sslaxx on 2011-05-31
> **samigina said:**
> Thats why ppas doesnt look so good for me...
Providing you use common sense they're OK. I have a few PPAs, and I do endeavour to make sure they're not malicious (OGRE3D, BennuGD).

---

### Post by Rasa1111 on 2011-05-31
> **Macskeeball said:**
> That command actually does more than that. It erases everything on any writable filesystem mounted at the time. It's not limited to the HD you're booted from.

 Yeah, thank god I didnt have my main partition mounted at the time.
Which I often do. 

> [COLOR=DarkOrange]**r.e.p.o.s. o.n.l.y.**[/COLOR] and you're safe 	

 safe and stuck with a fugly desktop. lol

In the year and a half Ive been using Ubuntu,
I have gotten all my themes from places like gnome-look and deviantART..
all without a hitch...
Until yesterday when I let my guard down and didnt ready* any* comments before downloading. . lol

so I think, as others are saying.. it's mostly
**[COLOR=DarkOrange]c.o.m.m.o.n. s.e.n.s.e.[/COLOR]** and you're safe. lol :P

I left my 'common sense' sword in its sheathe for the day...
and this is what happened. :P

 thanks all.

---

### Post by BigSilly on 2011-05-31
> **3Miro said:**
> I think he meant the official repos. Using unofficial repos is no different then downloading a .deb file.

Forgive my embarrassing noobness here, but I always thought that the public PGP keys and the checksums therein were there to protect the end user and foil this potential tainting of repos. My thoughts were that if someone were to upload a nasty app to the repositories, that this would result in a fault with the package manager at the users end because the keys wouldn't match, so you couldn't download anything until it had been fixed by the maintainers and the keys matched again.

I'm probably showing up my complete misunderstanding of how the repos work, but I could've sworn I'd read this somewhere.

---

### Post by 3Miro on 2011-05-31
> **BigSilly said:**
> Forgive my embarrassing noobness here, but I always thought that the public PGP keys and the checksums therein were there to protect the end user and foil this potential tainting of repos. My thoughts were that if someone were to upload a nasty app to the repositories, that this would result in a fault with the package manager at the users end because the keys wouldn't match, so you couldn't download anything until it had been fixed by the maintainers and the keys matched again.

I'm probably showing up my complete misunderstanding of how the repos work, but I could've sworn I'd read this somewhere.

The PGP key prevents a hacker from posing as the official repository and fooling your computer to install his/her own .deb. For example, without PGP key, I could use my machine to pretend to be the Canonical server and send you an "update" that will end up destroying your system. With the PGP key, your machine can easily spot an impostor. 

If a person working for Canonical enters bad code into a .deb file, the PGP key will do absolutely nothing. The point is that the Canonical repositories are not anonymous, they can track down anyone who has ever put a file in there and if a person were to do something malicious, he/she can be tracked down.

People posting on Gnome-looks are anonymous. Anyone from anywhere can make an account and post something. Almost all people there are honest users who want to share their art. However, there is no control and the place can and has been used by malicious people to try and damage other people's machines.

Unofficial repositories are a lot like Gnome-looks, someone put together some files on a server. Almost all unofficial ppa are honest people packaging and sharing software, unfortunately not all of them have good intentions.

---

### Post by tgm4883 on 2011-05-31
> **BigSilly said:**
> Forgive my embarrassing noobness here, but I always thought that the public PGP keys and the checksums therein were there to protect the end user and foil this potential tainting of repos. My thoughts were that if someone were to upload a nasty app to the repositories, that this would result in a fault with the package manager at the users end because the keys wouldn't match, so you couldn't download anything until it had been fixed by the maintainers and the keys matched again.

I'm probably showing up my complete misunderstanding of how the repos work, but I could've sworn I'd read this somewhere.

For the official repos, each package is signed by the uploader. Packages in the official repos have to be uploaded by approved members, which in turn review the packages from normal joes before uploading. The key for these repos is installed in Ubuntu by default.

For unofficial repos, you would have to either install the key manually, or manually give your OK to install unauthenticated packages. The warning message comes up when you attempt to install the package.

---

### Post by Macskeeball on 2011-05-31
> **Rasa1111 said:**
> Yeah, thank god I didnt have my main partition mounted at the time.
Which I often do. 

Or a backup drive. Or a remote file share from work. Or photos.

---

### Post by santaslittlehelper on 2011-05-31
That's just sad. In my mind gnome-look was a trusted site for whatever reason - I am goofy I guess - schema renewed.

---

### Post by Rasa1111 on 2011-05-31
> **Macskeeball said:**
> Or a backup drive. Or a remote file share from work. Or photos.


 damn, you're right...
The more I think about it the more I'd like to wrap my hands around that sad little persons neck and squeeze until all the squeeze is gone.. :twisted:

But on a better note..
I've finally got my ThinkPad running nothing but 11.04.
Something Ive been thinking about for awhile..
 Just couldn't bring myself to remove 10.10.
But since this little fiasco made it "impossible" to even boot into my 10.10 side.. (and I didnt know how to fix it)
 but all the files were still there, so I just saved my files and did a full 11.04 install. 

i like not having the grub menu on boot up. lol

 and to the little puke who did this.. (if you're still reading)
I've put a call out into the Universe to destroy you, i hope you enjoy it when it comes. lol :P 
....though it would appear with your sad little life you've already been destroyed, for the most part. 

 Good luck loser. lol

---

### Post by Irihapeti on 2011-05-31
I don't like the idea of "official Canonical repos only". I find it too restrictive.

It's also hard on beginning software developers. How are you going to get anyone to test / use your new program if it's already got to be in an official repo before anyone wants to touch it? That seems to me to be slightly against the spirit of open source where anyone can publish without needing to have the blessing of a large organisation.

Fortunately, there's one thing we can do to minimise the risk of using stuff from other places.

Make sure that nothing else is mounted before you play, and **[COLOR="Red"]HAVE A RECENT BACKUP[/COLOR]**.

I've messed up my system on a number of occasions and I've been able to restore in about half an hour or less. It really does work.

---

### Post by tjwoosta on 2011-05-31
> **Irihapeti said:**
> I don't like the idea of "official Canonical repos only". I find it too restrictive.

It's also hard on beginning software developers. How are you going to get anyone to test / use your new program if it's already got to be in an official repo before anyone wants to touch it? That seems to me to be slightly against the spirit of open source where anyone can publish without needing to have the blessing of a large organisation.



Open source means people can read through all of the code, compile it, and build packages themselves. Precompiled and packaged .deb's that are hosted in unofficial repositories are dangerous, source code that you check over yourself is not, assuming of course that you know how to read the code.

---

### Post by Tibuda on 2011-05-31
> **tjwoosta said:**
> Open source means people can read through all of the code, compile it, and build packages themselves. Precompiled and packaged .deb's that are hosted in unofficial repositories are dangerous, source code that you check over yourself is not, **assuming of course that you know how to read the code**.
> **tjwoosta said:**
> **[SIZE="3"]assuming of course that you know how to read the code[/SIZE]**
> **tjwoosta said:**
> **[SIZE="4"]assuming of course that you know how to read the code[/SIZE]**

The user base at which Ubuntu aims itself does not know how to read code.

---

### Post by Quadunit404 on 2011-05-31
And this is why I always check over the comments on something and the ratings before downloading, if they are available. Moral of this thread: never get a theme from a .deb without checking it over first.

Remember, the best antivirus in the world and the biggest security risk is a few feet in front of your computer screen.

Thanks for the warning, Rasa, although it's probably a bit late now as it was removed :P

---

### Post by JRV on 2011-05-31
Gnome look took it down, it now says "Content not found".

---

### Post by tjwoosta on 2011-05-31
> **Tibuda said:**
> The user base at which Ubuntu aims itself does not know how to read code.

Well theres no way around that Im afraid. If you cant read the code then how are you supposed to trust some random persons software? Thats why people who dont know what theyre doing should stick to the official repositories. Either that or rely on the comments and hope the other people know what theyre doing. And hope the person hosting the software didnt create a bunch of bogus accounts to comment on his own stuff and make it look legit.

---

### Post by Rasa1111 on 2011-05-31
> **Tibuda said:**
> The user base at which Ubuntu aims itself does not know how to read code.

Sad but true. 
I am one of the guilty . :???:

I would have known what the command in the file meant,  and a few other lines of bad code.. but the majority of it I am lost on. O_o
but I did not know that i needed to open up the .deb to make sure everything was alright.
I became to trusting and too "used to" good .deb packages. , 
and careless. 
Guess there's a time to learn it all eh. lol

---

### Post by forrestcupp on 2011-05-31
> **santaslittlehelper said:**
> That's just sad. In my mind gnome-look was a trusted site for whatever reason - I am goofy I guess - schema renewed.Like others have said, the only thing you can completely trust are the official repos. But sometimes expanded usability and upgrades are worth a little risk.

But you have to give gnome-look credit for getting it off their site fairly quickly.

> **Tibuda said:**
> The user base at which Ubuntu aims itself does not know how to read code.I know how to read some code, but that doesn't mean I have time to sift through tens of thousands of lines of code trying to figure out their programming style and how they set things up every time I install a program.

---

### Post by ikt on 2011-05-31
*cough*[http://ubuntuforums.org/showthread.php?t=1765542](http://ubuntuforums.org/showthread.php?t=1765542)*cough*

---

### Post by tjwoosta on 2011-05-31
> **forrestcupp said:**
> 
I know how to read some code, but that doesn't mean I have time to sift through tens of thousands of lines of code trying to figure out their programming style and how they set things up every time I install a program.

Thankfully most random unsupported stuff is not that large. The larger projects usually make it to the repos. Even if they dont they're at least fairly well known in the linux community, and the authors are fairly reputable. Also they're usually collaborations from a team of developers and its pretty safe to assume that at some point someone somewhere along the way would have noticed malicious code. I mean when is the last time you heard of someone finding malicious code hidden in a fairly large open source app? Its not that nobody ever reads the code, its that no reputable programmers are dumb enough to try it with open source. Its always script kiddies that do stupid stuff like that.

But I know if I were to try something malicious I would probably leave it out of the distributed source code, and just pre-package some binaries with the malicious bits. They would look and act like normal, but maybe have keylogger that runs in the background or something that most average users wouldnt notice.

---

### Post by ikt on 2011-05-31
> **tjwoosta said:**
> Thankfully most random unsupported stuff is not that large. The larger projects usually make it to the repos. Even if they dont they're at least fairly well known in the linux community, and the authors are fairly reputable. Also they're usually collaborations from a team of developers and its pretty safe to assume that at some point someone somewhere along the way would have noticed malicious code. I mean when is the last time you heard of someone finding malicious code hidden in a fairly large open source app? Its not that nobody ever reads the code, its that no reputable programmers are dumb enough to try it with open source. Its always script kiddies that do stupid stuff like that.

But I know if I were to try something malicious I would probably leave it out of the distributed source code, and just pre-package some binaries with the malicious bits. They would look and act like normal, but maybe have keylogger that runs in the background or something that most average users wouldnt notice.

I personally would be open for canonical having an online desktop customisation portal, where wallpapers and theme's are submitted and checked, like programs are with the software centre.

---

### Post by lucazade on 2011-06-08
[B]NEW WARNING!!! 
[/B]
Avoid to download this .deb
It is the same stuff of the other day :D

[http://gnome-look.org/content/show.php/The+KickAss+Project?content=142538](http://gnome-look.org/content/show.php/The+KickAss+Project?content=142538)

I've downloaded and extracted the archive just to see how stupid is the author

:lolflag:


I don't have an account on gnome-look.org.. please report it as bad content!!

---

### Post by Random_Dude on 2011-06-08
Again?
Could it be the same guy?

---

### Post by Irihapeti on 2011-06-08
> **Random_Dude said:**
> Again?
Could it be the same guy?

I think it's the same package with a different name.

How many times will this have to happen before the gnome-look admins start checking uploads?

---

### Post by Random_Dude on 2011-06-08
> **Irihapeti said:**
> I think it's the same package with a different name.

How many times will this have to happen before the gnome-look admins start checking uploads?

Probably not until the community applies some pressure.
Checking every single package is a lot of work but they should do it.

At least they could block the upload of .deb packages, IMHO.

---

### Post by HappinessNow on 2011-06-08
> **BigCityCat said:**
> 

The great thing is if you keep your data backed up it's a free and quick reinstall.Sounds like a good argument to use Chrome OS...also

...it is a shame that there are those kind of people out there that do this sort of thing.

Thanks for the Warning

---

### Post by Irihapeti on 2011-06-08
> **lucazade said:**
> [B]NEW WARNING!!! 
[/B]


It's been removed - quicker this time, I think.

---

### Post by Random_Dude on 2011-06-08
> **Irihapeti said:**
> It's been removed - quicker this time, I think.

Far quicker.
Good to see that they are starting to get on their toes.

---

### Post by CraigPaleo on 2011-06-08
> **Irihapeti said:**
> I think it's the same package with a different name.

How many times will this have to happen before the gnome-look admins start checking uploads?

I'm not a programmer but it seems like it wouldn't be difficult to write a program or script that automatically checks uploads for malicious commands. Then, the maintainers would only have to check the "flagged" uploads and not every single one of them.

---

### Post by Irihapeti on 2011-06-08
> **CraigPaleo said:**
> I'm not a programmer but it seems like it wouldn't be difficult to write a program or script that automatically checks uploads for malicious commands. Then, the maintainers would only have to check the "flagged" uploads and not every single one of them.

I'm not a programmer either - I can put together some bash scripts which I'd be ashamed to show to anyone else. :) I am happy to leave the details of how they do this to the admins, as long as something gets done. After all, saving some time by not checking isn't much use if your site gets ignored because people don't trust it.

---

### Post by tgm4883 on 2011-06-08
> **CraigPaleo said:**
> I'm not a programmer but it seems like it wouldn't be difficult to write a program or script that automatically checks uploads for malicious commands. Then, the maintainers would only have to check the "flagged" uploads and not every single one of them.

well that could actually get kinda complicated. They should just restrict uploads to .tar.gz, then easily grep any scripts for malicious commands

The issue then is who keeps the list, what is considered a malicious command, etc. 

From a liability standpoint, it's better to say "untested: use at your own risk" than it is to say "we checked these for malicious commands, and they didn't have any commands that we consider malicious". If they did say that, it gives a false sense of security to the user and as a programmer there are many ways around those types of filters.

For instance, how would you get a script to find this rm command? (note part 6 could obviously be a malicious dir)

```
#!/bin/bash

part1="r"
part2="m"
part3="-"
part4="r"
part5="f"
part6="testdir"

$($part1$part2 $part3$part4$part5 $part6)
```

---

### Post by Rasa1111 on 2011-06-08
> **ikt said:**
> *cough*[http://ubuntuforums.org/showthread.php?t=1765542](http://ubuntuforums.org/showthread.php?t=1765542)*cough*

 sweet! thanks!! :KS

lucazade, good catch! <3

---

### Post by CraigPaleo on 2011-06-08
> **Irihapeti said:**
> I'm not a programmer either - I can put together some bash scripts which I'd be ashamed to show to anyone else. :) I am happy to leave the details of how they do this to the admins, as long as something gets done. After all, **saving some time by not checking isn't much use if your site gets ignored because people don't trust it**.

Exactly. It may not even be a matter of saving time but simply having the time. I don't know how much gets uploaded daily but it might be a hefty chunk of data to go through.

> **tgm4883 said:**
> well that could actually get kinda complicated. They should just restrict uploads to .tar.gz, then easily grep any scripts for malicious commands

The issue then is who keeps the list, what is considered a malicious command, etc. 

It might not be as simple as I thought but I was thinking more along the lines of automation. No single person would keep the list and the maintainers would agree upon what malicious code is.

> **tgm4883 said:**
> From a liability standpoint, it's better to say "untested: use at your own risk" than it is to say "we checked these for malicious commands, and they didn't have any commands that we consider malicious". If they did say that, it gives a false sense of security to the user and as a programmer there are many ways around those types of filters.

You don't have to claim anything by adding extra measures of protection. All it would or could do is help keep people from downloading malicious scripts from the "look" sites. Once one person has had that awful experience, the word gets out as a warning as we can see in this very thread. 

> **tgm4883 said:**
> For instance, how would you get a script to find this rm command? (note part 6 could obviously be a malicious dir)

```
#!/bin/bash

part1="r"
part2="m"
part3="-"
part4="r"
part5="f"
part6="testdir"

$($part1$part2 $part3$part4$part5 $part6)
```

I honestly have no clue. ;) I would hope someone could come up with something that could detect that sort of thing. :)

---

### Post by Irihapeti on 2011-06-08
I suppose they could have a list of trusted contributors, a bit like Ubuntu members on this forum. Their stuff wouldn't need to be checked.

Of course, for all I know, these long-term contributors might be relatively few, and most of the stuff contributed by relative newcomers. Then that wouldn't really solve much.

And I'm going to bang my boring old drum again and say that a **[COLOR="Red"]recent backup is always a good idea[/COLOR]**. It's not only malicious software that can leave you with a real mess to clean up. (Been there, done that ... can't remember how many times now.)

---

### Post by 3Miro on 2011-06-08
The more I think about it the more convinced I become that banning .deb and scripts is the best option for Gnome-looks. Gnome comes with a great drag'n'drop feature for installing themes, which is safe since nothing gets executed (as root or otherwise). There is no real need for scripts and .deb files.

---

### Post by CharlesA on 2011-06-08
> **3Miro said:**
> The more I think about it the more convinced I become that banning .deb and scripts is the best option for Gnome-looks. Gnome comes with a great drag'n'drop feature for installing themes, which is safe since nothing gets executed (as root or otherwise). There is no real need for scripts and .deb files.
+9000. That would be the best way to do it imho.

---

### Post by swoll1980 on 2011-06-08
> **PhillyPhil said:**
> Rasa, google his user name.  It gives his real name and twitter account as the first hit.

Is it against the law? If not it should be; messing peoples' things up I mean.

---

### Post by CraigPaleo on 2011-06-08
> **swoll1980 said:**
> Is it against the law? If not it should be; messing peoples' things up I mean.

It's just as illegal as burning someone's physical files or placing a board of nails behind someone's car tires.

---

### Post by CraigPaleo on 2011-06-08
> **3Miro said:**
> The more I think about it the more convinced I become that banning .deb and scripts is the best option for Gnome-looks. Gnome comes with a great drag'n'drop feature for installing themes, which is safe since nothing gets executed (as root or otherwise). There is no real need for scripts and .deb files.

If that's true, I agree but when I used Gnome, there were some themes that couldn't be installed without installing a theme engine, some of which weren't available in the repos, and using the command line to install the rest. This was Gnome 2 though. If that's changed, great! It sounds not too dissimilar to the way KDE does it from within. 

> **CharlesA said:**
> +9000. That would be the best way to do it imho.
+9001!

---

### Post by Roasted on 2011-06-08
when gnome-look meets suicide linux. nice.

[http://qntm.org/suicide](http://qntm.org/suicide)

---

### Post by swoll1980 on 2011-06-08
> **Roasted said:**
> when gnome-look meets suicide linux. nice.

[http://qntm.org/suicide](http://qntm.org/suicide)

It's to bad there isn't a download for it.

---

### Post by Roasted on 2011-06-10
> **swoll1980 said:**
> It's to bad there isn't a download for it.

There is, somewhere. I had seen it on a different (and more official looking) web site about a year or two ago.

I think a distro of this nature of perfectly acceptable for a critical-application production server.

---

### Post by sourchier on 2011-06-22
I wonder if we could change dpkg to fail (with a warning) whenever a user tries to install scripts like this. Anyone in the know care to comment?

---

### Post by dniMretsaM on 2011-06-22
I don't know if it's possible to have dpkg detect the contents of a script before it runs it, but it sounds plausible. And that is a pretty good idea. Maybe it could come up with a warning something like this:
```
WARNING: Dpkg has detected a potentially malicious script. Please inspect the contents of this package. If you have already done so and want to install anyway, type 'yes'. Otherwise, type 'no'.
```

---

### Post by 3Miro on 2011-06-22
dpkg needs to have access to the system in more than one way. Even if you guard against simple commands (like delete all), there is no way to protect against attacks in general.

I don't think we can make this work.

---

### Post by tgm4883 on 2011-06-22
> **3Miro said:**
> dpkg needs to have access to the system in more than one way. Even if you guard against simple commands (like delete all), there is no way to protect against attacks in general.

I don't think we can make this work.

It would have to be an ever evolving list of bad things. It could also analyze behavior and attempt to prevent bad things that weren't on the list. And if built into dpkg, that would only matter for things installed through dpkg, what about everything else? Better to make it a separate application.

Awesome, just created an antivirus application

---

### Post by 3Miro on 2011-06-22
> **tgm4883 said:**
> It would have to be an ever evolving list of bad things. It could also analyze behavior and attempt to prevent bad things that weren't on the list. And if built into dpkg, that would only matter for things installed through dpkg, what about everything else? Better to make it a separate application.

Awesome, just created an antivirus application

Yes, you are right.

The list of "suspicious" behavior would have to be constantly updated, meaning that it would certainly lag behind. Furthermore, you will have to deal with an enormous amount of false-positives.

This is not a solution to anything.

---

### Post by Linuxratty on 2011-06-22
has anyone contacted the scumbag who did this?

---

### Post by Rasa1111 on 2011-06-22
> **Linuxratty said:**
> has anyone contacted the scumbag who did this?

 I made the attempt. 
but like the little coward he is, he stayed in his cave and kept his lid shut.
 (aka moms basement) :mad:

---

### Post by sourchier on 2011-06-23
Adding a sanity check that doesn't allow dpkg to run "rm" isn't anti-virus IMHO.
I also remember there was a bad screensaver script on gnome-look.org.I wonder if the site has been compromised?

---

### Post by 3Miro on 2011-06-23
> **sourchier said:**
> Adding a sanity check that doesn't allow dpkg to run "rm" isn't anti-virus IMHO.
I also remember there was a bad screensaver script on gnome-look.org.I wonder if the site has been compromised?

Except "rm" is needed for uninstalling things as well as fixing some settings files. Then even if they don't allow rm, then you can do other things that are just as damaging.

---

### Post by tgm4883 on 2011-06-23
> **sourchier said:**
> Adding a sanity check that doesn't allow dpkg to run "rm" isn't anti-virus IMHO.
I also remember there was a bad screensaver script on gnome-look.org.I wonder if the site has been compromised?

There are many things that dpkg could do that would be bad. I mean, it can put in a cron job then do anything it wants. Your sanity check is now irrelevant.

---

### Post by sanderd17 on 2011-06-23
A long thread, didn't read it all, but what do you guys think of this: [http://www.webupd8.org/2011/06/gnome-shell-extensions-to-get-website.html#more](http://www.webupd8.org/2011/06/gnome-shell-extensions-to-get-website.html#more)

It might be worth looking into the security once it is out.

What I would like against malware is as in Android: a normal user can install programs without being root and those programs have to ask permissions before they can do something.

Possible perissions:
[LIST]
[*]read other files than their install directory
[*]connect to the internet
[*]use webcam
[*]...
[/LIST]

Off coarse root can still install anything and has all permissions, the root account doesn't have to be blocked like in Android.

---

### Post by tgm4883 on 2011-06-23
> **sanderd17 said:**
> A long thread, didn't read it all, but what do you guys think of this: [http://www.webupd8.org/2011/06/gnome-shell-extensions-to-get-website.html#more](http://www.webupd8.org/2011/06/gnome-shell-extensions-to-get-website.html#more)

It might be worth looking into the security once it is out.


Maybe I missed it, but how does that differ from a repository? It's still reviewed by someone in order to be listed there but that doesn't solve the problem of downloading and installing things from 3rd party sites.

---

### Post by lasm2000 on 2011-06-26
A very naive question. Isn't app armor supposed to stop this kind of things? I mean, the deb installer certainly has a lot of capabilities that must be enabled for it to work. But simple attacks as a sudo -Rf shouldn't be allowed at all, not even for a distro installer which works rather by setting the mount points of partitions.

---

### Post by Lucradia on 2011-06-26
> **lasm2000 said:**
> A very naive question. Isn't app armor supposed to stop this kind of things? I mean, the deb installer certainly has a lot of capabilities that must be enabled for it to work. But simple attacks as a sudo -Rf shouldn't be allowed at all, not even for a distro installer which works rather by setting the mount points of partitions.

gnome themes don't use deb all the time, and you can disguise a theme to run malicious code by just copying the theme manually and trying to apply it.

---

### Post by tgm4883 on 2011-06-26
> **Lucradia said:**
> gnome themes don't use deb all the time, and you can disguise a theme to run malicious code by just copying the theme manually and trying to apply it.

Combine that with the fact that real attacks wouldn't bother deleting everything on the disk. It would turn the machine into a zombie computer ready to DDOS someone.

---

### Post by nerdy_kid on 2011-06-26
Ok that's it, I am now reading the install scripts (and comments) on every deb I download from the the *-look sites...

---

### Post by trizrK on 2011-06-26
> **Rasa1111 said:**
> Just a friendly warning to anyone who visits gnome-look. 
[COLOR=Red]INSTALLING THIS WILL DELETE YOUR HDD[/COLOR]~ [http://gnome-look.org/content/show.php/Appows+%28gives+new+life+to+yur+Ubuntu%29?content=142208](http://gnome-look.org/content/show.php/Appows+%28gives+new+life+to+yur+Ubuntu%29?content=142208)
[SIZE=3][B]
So do not use it. [/B][/SIZE]

One of the very few times I installed something from there without looking at the comments first..
and it wiped my entire 11.04-Natty partition. 

My 10.10 partition is intact, but it completely destroyed my 11.04 side. 

So,
 This just goes to show that even if your are usually quite vigilante.. 
You can still slip up and screw yourself. 
Like i just did. 

Be careful. 
Out there be *scumbag* monsters... :???:
Looks like it's been taken down

---

### Post by doas777 on 2011-06-26
I was looking for themes just yesterday, and it was very hard to find any that did not require the user to add a ppa. I can understand avoiding debs and ppas, but its hard when thats the only option.

---

### Post by Rasa1111 on 2011-06-27
> **trizrK said:**
> Looks like it's been taken down

Yeah, like 6 or so hours after I made this thread.

---

### Post by Rasa1111 on 2011-06-27
> **doas777 said:**
> I was looking for themes just yesterday, and it was very hard to find any that did not require the user to add a ppa. I can understand avoiding debs and ppas, but its hard when thats the only option.

I rarely have to use/add a PPA for themes. 
Only themes Ive ever added a PPA for was Orta. 
But I have and download lots of themes..
and really ever need to use a PPA to get/use them. 

I actually only recall seeing very few themes with a PPA.

---

