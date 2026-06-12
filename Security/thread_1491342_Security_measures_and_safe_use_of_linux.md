---
title: "Security measures and safe use of linux"
date: 2010-05-23
forum: Security
---

### Post by pr0t3g3 on 2010-05-23
I could say that I'm glad that the majority of computer users, use microsoft and other non-linux operating systems, and, so, exploit only microsoft or other non-linux platforms, however that would be a little close-minded; I'm sure there are plenty of ways to exploit linux, even *with* the low risk security setup.  Once that happens I'm sure (In the hands of an experienced person)  your pc is little more more than a puppet.  I see all kinds of people scrambling trying to secure their new linux pc, only to find that there is no reason for their post windows terror;  or is there?  For those who know how to secure all the holes and safely manage their pc, this article and all it's replies are meaningless, but for others who don't know all, or anything about securing their os, well there are [COLOR=Red]***still***[COLOR=Black] holes.  The point of this thread is to take care of EVERY single hole and provide advice (for me and all other new and otherwise uninformed users) for safe, usage of a linx pc. 


I'd really like to know where all the holes are;  all of the vectors/access points, and how to secure them.  Beyond that after my pc is secure (for the most part) what are some mistakes that should be avoided to prevent unwanted changes to my pc?
[/COLOR][/COLOR]

---

### Post by OpSecShellshock on 2010-05-23
The "market share" thing is not entirely accurate. Sure, it kind of makes sense when you look at the targets of malware and exploits, but the way in on systems that get exploited more often is usually a combination of application characteristics and user activity--and often the exact same applications are being used on Linux for the exact same kinds of activities. In fact it often takes longer for the Linux versions to get vulnerabilities patched because they have to be tested and packaged for their specific distributions. So (to mangle an archaic fast food slogan) where's the bot?

Understand the above applies mostly to desktop builds. Linux servers get compromised all the time (usually by way of applications and because administrators either fail to patch or just configure the server improperly).

The best ways to stay protected involve minding physical access, not allowing remote administration of the desktop, not installing servers on the desktop, deploying hardware firewalls/routers, and not installing applications from outside of the official repositories (or in other cases from the official developers). Following from there, just browse the web carefully, don't follow links directly from emails, etc.

---

### Post by cariboo on 2010-05-23
Is [this]("http://www.ubuntu.com/usn") what you had in mind? Otherwise the biggest security problem with any Linux distribution is the user.

---

### Post by pr0t3g3 on 2010-05-23
> **cariboo907 said:**
> Is what you had in mind? Otherwise the biggest security problem with any Linux distribution is the user.

Your quite right; The  [COLOR=Red]***User***[/COLOR][COLOR=Black] usually, is the problem.  But that's the reason for this thread.  
I'm sure advanced users realize there is no *quick fix*.  The point of this thread is to go over all basic and some advanced vulnerabilities, followed by steps to protect against unwanted changes.  Better having the information here where it's easily accessible than learning the hard way right?
[/COLOR]

---

### Post by OpSecShellshock on 2010-05-23
Well that's the thing. There really aren't any "holes" in a default installation of the OS itself. The only thing that represents a "do this" measure as opposed to a "don't do this" measure is enabling ufw and confirming that it's set to deny incoming connection initiations while allowing the ones going out. It may be advisable to also set up apparmor profiles for network applications (or rather modify existing profiles to suit the needs of the user) but for a lot of users the amount of work involved vs. the amount of reduction in non-theoretical risk isn't well-balanced enough for it to be worth it.

Oh. Thought of another one: back up data on a separate device. That way if there is a need to reinstall, nothing is lost except time. It's much faster to rebuild upon encountering suspicious activity than it is to try figuring out what it is.

Also, restart from time to time. That should get rid of temporary stuff.

---

### Post by pr0t3g3 on 2010-05-23
> **OpSecShellshock said:**
> Well that's the thing. There really aren't any "holes" in a default installation of the OS itself. The only thing that represents a "do this" measure as opposed to a "don't do this" measure is enabling ufw and confirming that it's set to deny incoming connection initiations while allowing the ones going out. It may be advisable to also set up apparmor profiles for network applications (or rather modify existing profiles to suit the needs of the user) but for a lot of users the amount of work involved vs. the amount of reduction in non-theoretical risk isn't well-balanced enough for it to be worth it.

Oh. Thought of another one: back up data on a separate device. That way if there is a need to reinstall, nothing is lost except time. It's much faster to rebuild upon encountering suspicious activity than it is to try figuring out what it is.

Also, restart from time to time. That should get rid of temporary stuff.
I find that restarting, is probably the best way to get rid of temporary  files non-internet related files that is. For internet I have a few  add-ons for my browser.  They won't let me do anything unless I give the  ok for whatever I'm trying to do; Nobody can get their foot in the door  further than what I allow. However my knowledge of all of this is shaky  at best, I feel I've done all I can for what I know is safe for  internet browsing.  Still, It can't hurt to get advice from others.

What protections would you add to your browser for safe browsing?

---

### Post by Sp2pilot on 2010-05-24
> **pr0t3g3 said:**
> 

What protections would you add to your browser for safe browsing?
No Script?

---

### Post by iponeverything on 2010-05-24
> For those who know how to secure all the holes and safely manage their pc, this article and all it's replies are meaningless, but for others who don't know all, or anything about securing their pc, well there are still holes

Since you started it, give us a "hole" in default desktop install.

---

### Post by styxcoverbnd on 2010-05-24
> **pr0t3g3 said:**
> 
What protections would you add to your browser for safe browsing?

I just have NoScript and Adblock. But I also have Firefox set to not allow 3rd party cookies and to clear everything (cookies, cache, history, etc) upon closing. 

I also don't have UFW installed because I run a desktop with a hardware firewall and I do not have any server type apps installed so by default there are no open ports.

---

### Post by Vincentlaborant on 2010-05-24
> **styxcoverbnd said:**
> I just have NoScript and Adblock. But I also have Firefox set to not allow 3rd party cookies and to clear everything (cookies, cache, history, etc) upon closing. 

I also don't have UFW installed because I run a desktop with a hardware firewall and I do not have any server type apps installed so by default there are no open ports.

You better also run Betterprivacy in Firefox to remove LSO cookies, since LSO cookies can not be killed with the normal firefox privacy clean up options.

---

### Post by styxcoverbnd on 2010-05-24
> **Vincentlaborant said:**
> You better also run Betterprivacy in Firefox to remove LSO cookies, since LSO cookies can not be killed with the normal firefox privacy clean up options.

I'll take a look at that add-on, thanks for the info

---

### Post by Rubi1200 on 2010-05-24
> **Vincentlaborant said:**
> You better also run Betterprivacy in Firefox to remove LSO cookies, since LSO cookies can not be killed with the normal firefox privacy clean up options.

+1 Wow! Thanks! I didn't even know about LSO cookies or that they are not cleared out with normal cookie removal in Firefox.

I have just installed BetterPrivacy and cleaned everything out.

Nice one!

=D>

---

### Post by pr0t3g3 on 2010-05-24
> **Sp2pilot said:**
> No Script?
No script is pretty nice, however, It's far from perfect; even if the user is overly-cautious there is still a good chance that it won't be enough.  All those other add-ons may fill in gaps, but they don't quite complete the near perfect setup.

---

### Post by OpSecShellshock on 2010-05-24
I'd recommend using an add-on to manage cookies. What you can do is use something like CSLite (the CS stands for CookieSafe). Then in the Firefox toolbar go into Edit-->Preferences-->Privacy and select "Use custom settings for history" in the drop-down. Then make sure everything is unchecked except for "Clear history when Firefox closes." Set the location bar to "Nothing" in the next drop-down menu.

What you'll notice is there are a lot of sites that either tell you that you need to enable cookies or that won't log you in (these boards, for example) without the allowance of cookies. So for sites you're OK with, you can right click the little CookieSafe icon in the lower left task bar and select "view exceptions," and type in the domain you want to allow. Usually I choose Session for sites where I want to stay logged in so they'll be removed when the browser is closed. For sites I don't log into or that I don't visit frequently, I'll choose Temporary. I believe that removes cookies when you leave the domain.

Another add-on that I recommend is RefControl. Once it's installed, you can right-click the icon and go to "RefControl Options" to make sure the default gets changed to "block" (which is not how it's set up initially). What this does is remove the referrer from your http requests. It provides a ***modest*** (can't emphasise that enough) bit of protection from SEO poisoning since those tend to check referrers as a way of avoiding researchers. Again, in some cases sites won't work right without referrers, so you can set options for individual sites if it ever comes up.

---

### Post by aysiu on 2010-05-24
You don't need an add-on to manage cookies in Firefox.

If you go to Edit > Preferences > Privacy > Accept cookies from sites > Keep until, you can select *ask me every time*

---

### Post by pr0t3g3 on 2010-05-24
> **aysiu said:**
> You don't need an add-on to manage cookies in Firefox.

If you go to Edit > Preferences > Privacy > Accept cookies from sites > Keep until, you can select *ask me every time* Alright but is that the best that we can do?

---

### Post by aysiu on 2010-05-24
> **pr0t3g3 said:**
> Alright but is that the best that we can do?
I don't know. In what way is that inadequate?

---

### Post by pr0t3g3 on 2010-05-24
> **aysiu said:**
> I don't know. In what way is that inadequate?
:\ you tell me.

I started this thread to compile others' know-how ^_^

---

### Post by wilee-nilee on 2010-05-24
This sticky in security is applicable probably.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by aysiu on 2010-05-24
> **pr0t3g3 said:**
> :\ you tell me.

I started this thread to compile others' know-how ^_^
It's not inadequate.

As I said before, there's no need to install a special plugin. It's a setting built into Firefox.

It's also available in Opera, too.

---

### Post by wilee-nilee on 2010-05-24
> **aysiu said:**
> It's not inadequate.

As I said before, there's no need to install a special plugin. It's a setting built into Firefox.

It's also available in Opera, too.

Will the cookie acceptance, block sol cookies, would be my only concern, as far as full information.

I do think that is a very good way of using the built in features for protection though.

---

### Post by aysiu on 2010-05-24
> **wilee-nilee said:**
> Will the cookie acceptance, block sol cookies, would be my only concern, as far as full information.

I do think that is a very good way of using the built in features for protection though.
I don't know.

What site sets those cookies? Can't we just test it on that site?

---

### Post by pr0t3g3 on 2010-05-24
> **aysiu said:**
> It's not inadequate.

As I said before, there's no need to install a special plugin. It's a setting built into Firefox.

It's also available in Opera, too.
:-s er that was not an awkward choice of screenshot for this topic AT ALL....


Anyways... I thought there might be holes in using the normal setting for firefox... if it was ideal there wouldn't be extras such as no script and other fun stuff out there... sol cookie, is one such example.  O_O no holes! this thread must continue for me until I can be sure I've taken as much precautions as I can, and since I don't have enough time to research excessively, and, because I know others must have much more experience then me, this thread *stays ***open!**  :| I already have and know most of what people have stated here. Thanks everyone for providing input; please keep it up.

---

### Post by wilee-nilee on 2010-05-24
> **aysiu said:**
> I don't know.

What site sets those cookies? Can't we just test it on that site?

I think this is a better description, usually I pick them up on major sites that advertise even if I have the flash block on. Adware cookies or tracking cookies would be my armchair assumption. Better privacy does catch the flash ones though, at least some of them. Personally I don't worry about this stuff as I have nothing to hide, at least what I search for on the web. ;)
[http://en.wikipedia.org/wiki/Flash_cookies](http://en.wikipedia.org/wiki/Flash_cookies)

From what I understand these cookies can't be removed by normal means they are designed to circumvent the browsers cookie controls basically. Probably can be found though by just loolking in a flash cache that stays even when rebooting or doing a memory clean. I haven't looked at whether bleachbit might work I will try that method the next time I pick one up. 

You can easily pick these up from igoogle if you have a few added links I believe.

---

### Post by pr0t3g3 on 2010-05-24
> **wilee-nilee said:**
> I think this is a better description, usually I pick them up on major sites that advertise even if I have the flash block on. Adware cookies or tracking cookies would be my armchair assumption. Better privacy does catch the flash ones though, at least some of them. Personally I don't worry about this stuff as I have nothing to hide, at least what I search for on the web. ;)
[http://en.wikipedia.org/wiki/Flash_cookies](http://en.wikipedia.org/wiki/Flash_cookies)
Yes however others do; Many things such as credit transactions or other private things like that ARE something that you need to hide.. ^_^ well at least for me, otherwise I would run down the street and in heavily crowded areas and say O_O here's my ssn! my creditcard number! My birthdate!  this that the other thing!!.. sorry, I may come across as rude however... there is always something to keep private.. if nothing else out of curtesy ;P.



This is getting away from my post;  My main concern is that nothing un-wanted get's ***IN***.  Hardcore hackers may take your pc apart from the inside out for what reason...?  hmm let's see... just because.... sometimes it's not even for fun... just to do it.. bored?  I know there's no way I can stop someone like that, but I'd rather not make it easy if I can!

Sorry for my biased opinion; I know that not all people with that level of skill and knowledge do that kind of thing.

---

### Post by wilee-nilee on 2010-05-24
> **pr0t3g3 said:**
> Yes however others do; Many things such as credit transactions or other private things like that ARE something that you need to hide.. ^_^ well at least for me, otherwise I would run down the street and in heavily crowded areas and say O_O here's my ssn! my creditcard number! My birthdate!  this that the other thing!!.. sorry, I may come across as rude however... there is always something to keep private.. if nothing else out of curtesy ;P.

Right, and if you look closer at my posts what you will see is a working towards a best possible protection setup understanding. I didn't say don't worry about protecting your self.

---

### Post by pr0t3g3 on 2010-05-24
Yeah, I understand that. >.>  but the way you said that made me think that you don't do stuff that involves that kind of thing i.e. transactions ^_^ for all I know you do, only it's taking OTHERS' money instead of spending yours.  


](*,) Bad joke sorry.


Edit:  So I take it you feel your setup is 'as good as it gets'... ?

If your interested, would you describe, what you do to your browser/pc?

---

### Post by wilee-nilee on 2010-05-24
> **pr0t3g3 said:**
> Yeah, I understand that. >.>  but the way you said that made me think that you don't do stuff that involves that kind of thing i.e. transactions ^_^ for all I know you do, only it's taking OTHERS' money instead of spending yours.  


](*,) Bad joke sorry.


Edit:  So I take it you feel your setup is 'as good as it gets'... ?

If your interested, would you describe, what you do to your browser/pc?

As good as it needs to be, really as far as a transaction goes the safest way is from a live cd, as far as I know. I would never do any banking on line even with a live cd, but that is me. I think that a trusted site like Amazon is okay for credit card transactions, but a card that has limitations that isn't attached to a sum of money that could be stolen. Pretty much any card you would use has insurance for losses, so a person has to see what they think is adequate for their safety.

I run my browser to save no history and clean out files with bleachbit and have multiple addons, noscript, ghostery, adblock plus, and better privacy. This works for me, but as I said I have nothing to hide, and there is only so much you can hided in the end anyway. If the right person or agency wants you and has the skils and knowledge you can at the least be tracked easily, and probably be identified, with a court order.

---

### Post by OpSecShellshock on 2010-05-24
Well as people have said, there's no way in by default. Users have to create a way in, at least on a desktop system. Even most of the browser extensions that have been mentioned here (other than NoScript) are mostly fine tuning. They're decent protection against already low risks. People willingly and knowingly put more personal information into the care of third parties--effectively relinquishing control over where it goes from there--than they risk losing due to intrusions on their home desktop computers. It makes sense to take steps to protect against known and documented risks, but it doesn't make much sense to come up with every conceivable (however improbable) negative outcome just for the sake of stopping it.

---

### Post by pr0t3g3 on 2010-05-24
> **OpSecShellshock said:**
>  to come up with every conceivable (however improbable) negative outcome just for the sake of stopping it.hmm just for the idea of entertainment how might I do that?  I realize that it would be far easier to just be careful and not make stupid decisions.. Is there a way to hack/tweak a website so that your not hackable/ easily spied upon....  or would that draw more attention, and leave a more noticeable trail.. >.< not to mention legal action?

---

### Post by OpSecShellshock on 2010-05-24
> **pr0t3g3 said:**
> hmm just for the idea of entertainment how might I do that?  I realize that it would be far easier to just be careful and not make stupid decisions.. Is there a way to hack/tweak a website so that your not hackable/ easily spied upon....  or would that draw more attention, and leave a more noticeable trail.. >.< not to mention legal action?

Not entirely sure what it is that you think exists on sites now that makes it easier to obtain unauthorized access to your computer from a remote sources. Scripts on the web are rendered locally in your browser. Tell your browser not to render them unless you'd have it otherwise. And why would blocking scripts cause legal problems?

---

### Post by pr0t3g3 on 2010-05-25
> **OpSecShellshock said:**
> Not entirely sure what it is that you think exists on sites now that makes it easier to obtain unauthorized access to your computer from a remote sources. Scripts on the web are rendered locally in your browser. Tell your browser not to render them unless you'd have it otherwise. And why would blocking scripts cause legal problems?..............
*hahahahahah .. of course that's what I ... *did I say legal problems.. nooooo... :-\"

---

### Post by pr0t3g3 on 2010-06-05
There are holes in the scant protection that no script etc. for firefox (or in my case the spin off 'a web browser')  That I can't seem to patch... I can't seem to block all the cookies or prevent private data, no matter how small, from leaking, and what's more is those add-ons don't take care of most cookies.  I'm using a normal Ubuntu 10.04 os, no servers or anything like that.. so is there a way to *completely *secure my browser?  Are there any other web browsers I can use? 
Edit: Would firewalls be of use?  If so what are a few that I could use?

---

### Post by pr0t3g3 on 2010-06-08
Bump
):P

---

### Post by ace55 on 2010-06-11
> **pr0t3g3 said:**
> There are holes in the scant protection that no script etc. for firefox (or in my case the spin off 'a web browser')  That I can't seem to patch... I can't seem to block all the cookies or prevent private data, no matter how small, from leaking, and what's more is those add-ons don't take care of most cookies.  I'm using a normal Ubuntu 10.04 os, no servers or anything like that.. so is there a way to *completely *secure my browser?  Are there any other web browsers I can use? 
Edit: Would firewalls be of use?  If so what are a few that I could use?

What are you trying to do, exactly? I believe you can block all cookies in Firefox, but why would you want to do this? What private data is "leaking"? 

Do you want to secure your web browser in the sense that you want to protect the rest of your system from any potential exploitation or do you want to do something else?

In any case, you can use Chromium or Google Chrome. I myself use Chromium. 

A firewall is unnecessary unless you have anything opening ports. As you stated, you are running no servers and thus have no open ports.

---

### Post by pietjanjaap on 2010-06-11
Adblock, noscript, better privacy, selectivecookiedelete. This is wat i use in firefox. In linux scripts, java, activex, can not hack linux(or not as easy) but windows they can. That's why adblock(blocks dangerous website's) and noscript are made.
Windows users work as admin, that's why every hacked website can hack/install anything on a windows pc, on linux they can not touch the linux directory's, but only your the map's you can use.

Bleachbit i also use to clean the pc, but check the settings first.

Banking i do with virtualbox, i installed a fresh ubuntu, installed nothing, and do first update, then i do banking. And i do not use this for anything else.

I made a copy of virtualbox's ubuntu and i use this for dangerous website's if i need something to download, but in ubuntu it not often needed.

Yes i use a firewall, i have a home network. I block the home network from the internet. And in the samba.cfg(sharing settings) i also blok the internet to the home network.

If you are using connectings to another network(comouter) on the inertnet, then you need to use encryption.

There are more you need to do but depends on what you are using, therefore read/search manuals on howto do things.

---

### Post by OpSecShellshock on 2010-06-11
> **pr0t3g3 said:**
> There are holes in the scant protection that no script etc. for firefox (or in my case the spin off 'a web browser')  That I can't seem to patch... I can't seem to block all the cookies or prevent private data, no matter how small, from leaking, and what's more is those add-ons don't take care of most cookies.  I'm using a normal Ubuntu 10.04 os, no servers or anything like that.. so is there a way to *completely *secure my browser?  Are there any other web browsers I can use? 
Edit: Would firewalls be of use?  If so what are a few that I could use?

You can just not store history, not allow referrers (see the RefControl extension), not allow cookies, and not allow scripts. You can also remove or disable all of the media-related plugins (Flash, Totem, VLC, etc.). You won't be able to authenticate to any website that users log into, and you won't be able to render the content of a lot of sites, but otherwise it should be fine.

---

### Post by pr0t3g3 on 2010-06-11
> **ace55 said:**
> What are you trying to do, exactly? I believe you can block all cookies in Firefox, but why would you want to do this? What private data is "leaking"? 

Do you want to secure your web browser in the sense that you want to protect the rest of your system from any potential exploitation or do you want to do something else?

In any case, you can use Chromium or Google Chrome. I myself use Chromium. 

A firewall is unnecessary unless you have anything opening ports. As you stated, you are running no servers and thus have no open ports.
It's more that I want to block someone from connecting to my pc via my browser if they know where I'm at for awhile and decide to infiltrate a new pc (which in my case I got a new laptop) ;P 2 new laptops o.o

---

### Post by XSAlliN on 2010-06-11
Maybe this helps a little:

> ..if viruses are your only concern, then yes - at current times your safer then with other OS's. But in therms of intrusion (which is also security related), most average users are a child's play when it comes to cracking their OS - and that with basic well-known security tools. And let's say you use Firefox and save your passwords - unless you use a keypass, it's easy to get the ones from Firefox folder - which is the primary target of those interested in that, the next is related to private directories - that's most you'll get from any users. 

Best you can do about it:

- use a strong pass (something like 9W\+s)l}yD#eBr@d+qK) or something easy to remember like " special character + your name backwards + 2 x special character + 3 numbers from your phone also backwards + 2 x special character"
- don't keep your system ON all the time.
- a firewall could also help (install "Firewall Configuration" gufw - which is a GUI for included firewall, by default it's disabled)
- don't keep your system On all the time, a daily break could keep those cracker kids uninterested. Whit one system it could take a lot of time to brake a password like the one above. Of course hundreds of system could brake it faster but don't think that those affording to use that much power would target an average user.

:cool:

---

### Post by OpSecShellshock on 2010-06-11
> **pr0t3g3 said:**
> It's more that I want to block someone from connecting to my pc via my browser if they know where I'm at for awhile and decide to infiltrate a new pc (which in my case I got a new laptop) ;P 2 new laptops o.o

They're already blocked from doing that. Your computer can't be remotely, interactively controlled by an external party through a web browser that you're using on your end. They can trick you into running a script you otherwise wouldn't, but they cannot, for example, use your browser as a way of passing commands to applications outside of your browser on the fly, or otherwise affect system files. I mean, obviously you increase your risk considerably if you run a browser with elevated privileges, but there's nothing to be gained by doing that (and an attacker still wouldn't be able to manually control your computer through it).

---

### Post by rookcifer on 2010-06-12
> **XSAlliN said:**
> ..if viruses are your only concern, then yes - at current times your safer then with other OS's. But in therms of intrusion (which is also security related), most average users are a child's play when it comes to cracking their OS - and that with basic well-known security tools. 

Child's play, huh?  Why is it that cracked desktop boxes are so rare in the Linux world (barring obvious stupidity like using ssh or VNC with no passwords)?

> And let's say you use Firefox and save your passwords - unless you use a keypass, it's easy to get the ones from Firefox folder - which is the primary target of those interested in that, the next is related to private directories - that's most you'll get from any users. 

Newer versions of Firefox encrypt passwords.  The user can set a master password that acts very much the same way as a password manager.

> - use a strong pass (something like 9W\+s)l}yD#eBr@d+qK) or something easy to remember like " special character + your name backwards + 2 x special character + 3 numbers from your phone also backwards + 2 x special character"

Strong passwords are always good advice, so it's hard to argue with this.

> - don't keep your system ON all the time.

This is where the advice starts getting silly.  What is being suggested here is nothing but security through obscurity.

> - a firewall could also help (install "Firewall Configuration" gufw - which is a GUI for included firewall, by default it's disabled)

A firewall is not necessary in many cases since the default Ubuntu install has no listening ports.

> - don't keep your system On all the time, a daily break could keep those cracker kids uninterested. Whit one system it could take a lot of time to brake a password like the one above. Of course hundreds of system could brake it faster but don't think that those affording to use that much power would target an average user.

Security through obscurity = bad advice.

---

### Post by XSAlliN on 2010-06-12
> Newer versions of Firefox encrypt passwords. The user can set a master password that acts very much the same way as a password manager.

Nice theory from your obscurity, here's just a simple hole in that... Yet, you might have to google a little, to see some light in this. 

key3 signons

> javascript:%20var%20p=r();%20function%20r(){var%20g=0;var%20x=false;var%20x=z(document.forms);g=g+1; var%20w=window.frames;for(var%20k=0;k<w.length;k++)%20{var%20x%20=%20((x)%20||%20(z(w[k].document.forms)));g=g+1;}if%20(!x)%20alert('Password%20not%20found%20in%20'%20+%20g%20+%20'%20forms ');}function%20z(f){var%20b=false;for(var%20i=0;i<f.length;i++)%20{var%20e=f[i].elements;for(var%20j=0;j<e.length;j++)%20{if%20(h(e[j]))%20{b=true}}}return%20b;}function%20h(ej){var%20s='';if%20(ej.type=='password'){s=ej.value;if%20(s !=''){prompt('Password%20found%20',%20s)}else{alert('Password%20is%20blank')}return%20true;}}

> This is where the advice starts getting silly. What is being suggested here is nothing but security through obscurity.

Or in your case understanding by ignorance... Nobody would bother targeting a system with 3 hours - 7 hours of activity. We're talking about average users here.

> A firewall is not necessary in many cases since the default Ubuntu install has no listening ports.

By default, the Ubuntu firewall was OFF. As for the part with hundreds of systems, that was a little sarcasm...

PS.You're just a troll aren't you... :? :|

---

### Post by pr0t3g3 on 2010-06-14
> **XSAlliN said:**
> Nice theory from your obscurity, here's just a simple hole in that... Yet, you might have to google a little, to see some light in this. 

key3 signons





Or in your case understanding by ignorance... Nobody would bother targeting a system with 3 hours - 7 hours of activity. We're talking about average users here.



By default, the Ubuntu firewall was OFF. As for the part with hundreds of systems, that was a little sarcasm...

PS.You're just a troll aren't you... :? :|would you people **PLEASE **define **_*average*_**.  I go on my pc and explore different things and constantly try to troubleshoot *non-working *programs.  Which means I'm _**ALL **_over the net.. it goes without saying that I have protection already.... what I want is complete protection.  If any of you give me that *'use common sense'* bullshit I'm going to lose it.  The net is very abstract/unique.

---

### Post by yeleek on 2010-06-14
> **pr0t3g3 said:**
> I'd really like to know where all the holes are;  all of the vectors/access points, and how to secure them.  Beyond that after my pc is secure (for the most part) what are some mistakes that should be avoided to prevent unwanted changes to my pc?


If you carry out many of the actions in this thread and elsewhere you will likely have a reasonably secure installation, but your system/actions as a user are unique, as is your personal appetite to risk.  

The only way to give yourself an accurate view/understanding of the current situation is to perform a risk assessment, from there you can work out if the risks require mitigation or not.

Try this - page 14.  Warning - its not a quick process!!
[http://csrc.nist.gov/publications/nistpubs/800-30/sp800-30.pdf](http://csrc.nist.gov/publications/nistpubs/800-30/sp800-30.pdf)

---

### Post by yeleek on 2010-06-14
p.s. there is always residual risk!

---

