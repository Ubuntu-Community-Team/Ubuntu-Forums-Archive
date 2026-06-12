---
title: "RMS: &quot;The Future of Free Software&quot;"
date: 2006-03-30
forum: The Cafe
---

### Post by darkmatter on 2006-03-30
Richard Stallman's keynote address on drafting GPL v3.

Transcript [**HERE**](http://www.fsfeurope.org/projects/gplv3/torino-rms-transcript.en.html)

Video [**HERE**](http://streaming.polito.it/TFOFS)

The current draft of GPL v3 can be found [**HERE**](http://gplv3.fsf.org/draft)

Read the transcript, watch the vid... leave comments/opinions.;)

---

### Post by prizrak on 2006-03-30
I think I understand why Linus doesn't want to switch the kernel to v3 now. IT would pretty much stop Linux on many things such as embedded devices or the TiVo he mentioned.

---

### Post by jrib on 2006-03-30
why can't tivo conform to gpl3?  What would it need to do?   I believe I don't understand the issue exactly.

I think the part that stops it, is DRM right?  What does tivo do that is DRM?  (I don't use tivo)

---

### Post by macrohard on 2006-03-30
I just wonder if this is the beginning of a split in the Linux community over all](*,)

---

### Post by argux on 2006-03-31
[QUOTE=_jason]why can't tivo conform to gpl3?  What would it need to do?   I believe I don't understand the issue exactly.

I think the part that stops it, is DRM right?  What does tivo do that is DRM?  (I don't use tivo)[/QUOTE]

It's in the transcript. As I understand it, and I might be wrong, tivo uses free software, but you can't modify it because if you try to use your own version of something on it, it won't run. It does some kind of checksum so that no other version but the one it comes with can be run.

I think the problem here is that linus or the developers or both don't want to risk tivo and any potential linux supporters going for non-free solutions, probably microsoft or the like, so they stay with GPLv2.

I also don't think this will be a split in linux community at all. The linux community already uses a great diversity of licenses which are more or less compatible with each other on a single OS. As RMS explains it, GPLv2 is compatible with the X11 licence, but not with the Mozilla licence. That doesn't stop anyone from using Firefox or Thunderbird on linux, or use Bugzilla on your GPL'ed project's site. A difference of versions of the same licence isn't likely to cause a split in a community. 

Think of the emacs vs. vi war. This doesn't keep people from working together in some project, or from being all part of the "linux community".

---

### Post by prizrak on 2006-03-31
[QUOTE=_jason]why can't tivo conform to gpl3?  What would it need to do?   I believe I don't understand the issue exactly.

I think the part that stops it, is DRM right?  What does tivo do that is DRM?  (I don't use tivo)[/QUOTE]
argux kinda explained it, I'll try to go into a bit more of a detail. It is in the transcript somewhere in the first half. 
What TiVo does is, it uses a customized and stripped down Linux (GNU/Linux) distribution with the proprietary software on top (the interface and PVR capabilities basically). Now TiVo is basically a computer, it has a TV tuner, an HDD a CPU and all that fun stuff. In order to prevent people from using anything else on that computer they digitally sign each of their OS's with a key that is uniquely generated. If the key on the hardware and key on the software correspond then the device works. If they do not it does not. This prevents you from being able to modify the software on the PVR itself to say include an ability to watch ogm videos on it or dl things from the internet. This is basically a violation of the GPL, the GPL says that any software can be modified by the user in any way as long as the changes are released to the community. It also says that you are allowed to use the software for anything you want, which it also prevents. That is the issue that RMS is trying to address. 

If Torvalds changes the kernel over to v3 TiVo would not be allowed to do that because it would be required to release the signature keys to the public so that you can use them when you do your modifications (basically the keys are obsolete). Torvalds doesn't want to switch over because that would very much stop companies like TiVo from using Linux and make them switch to either a proprietary OS or develop one in house. This is also true for other embedded devices, since alot of time manufacturers would have a more expensive version that does something a cheaper one doesn't.

---

### Post by htinn on 2006-03-31
TiVo *should* stop leeching off of our generous efforts of making the world a nicer OS than Wind'ohs! They really should decide whose side they're really on.

DRM is the betrayal of our trust, and goes against everything we believe in. As such, it deserves to be snubbed and circumvented at every available opportunity. If possible, it should be outlawed and the offenders (people who use DRM) should be sent to prison where they belong.

---

### Post by Sirin on 2006-03-31
[QUOTE=macrohard]I just wonder if this is the beginning of a split in the Linux community over all](*,)[/QUOTE]

There has been a split in the Linux community for a long time now. :???:

---

### Post by helpme on 2006-03-31
[QUOTE=Sirin]There has been a split in the Linux community for a long time now. :???:[/QUOTE]
:?:

---

### Post by htinn on 2006-03-31
Yeah, the "less filling" side vs. the "tastes great" side. OUR SIDE WILL WIN! Go LESS FILLING! ;)

---

### Post by Gadren on 2006-03-31
Even if Linus chose to switch Linux to GPL v3, he wouldn't be able to.  To do so would require appproval from all contributors to the code, which is nearly impossible.

---

### Post by imagine on 2006-03-31
[QUOTE=prizrak]If Torvalds changes the kernel over to v3 TiVo would not be allowed to do that because it would be required to release the signature keys to the public so that you can use them when you do your modifications (basically the keys are obsolete). Torvalds doesn't want to switch over because that would very much stop companies like TiVo from using Linux and make them switch to either a proprietary OS or develop one in house.[/QUOTE]Yes, that's exactly what needs to happen. You can't take software under the GPL, modify it, release it together with the sourcecode and announce that the users can do with it whatever they like, but if they change the program in any way they can't use it anymore.
That's free software ad absurdum.

If TiVo or whoever wants to develop proprietary software then they can do so. But not with the help of people who put their work under a copyleft licence.

---

### Post by jrib on 2006-03-31
[QUOTE=prizrak]If Torvalds changes the kernel over to v3 TiVo would not be allowed to do that because it would be required to release the signature keys to the public so that you can use them when you do your modifications (basically the keys are obsolete). Torvalds doesn't want to switch over because that would very much stop companies like TiVo from using Linux and make them switch to either a proprietary OS or develop one in house. This is also true for other embedded devices, since alot of time manufacturers would have a more expensive version that does something a cheaper one doesn't.[/QUOTE]

I remember reading that tivo was adding ads to the service.  So I suppose that if people were allowed to hack at the source and run it on their tivo boxes, they would just remove the ads from the code and then tivo will no longer have anyone interested in purchasing ads, and so tivo disappears.  

Now if that is the case, tivo can't really claim they are following the spirit of the gpl.  And I don't really see the point of linux using the gpl but catering to exceptions like tivo.  Either linux should use the gpl and do everything it can to ensure that people do not get around what the gpl promises by using loopholes (which what tivo does is exactly that, a loophole), or linux needs to use a different license that allows for things like tivo (not as a loophole against the spirit of the document).

---

### Post by ssam on 2006-03-31
as i understand it the tivo does not violate gpl2 because you can modify software, you just can't run modified software on the hardware.

in some cases this is a very useful feature. i could have a server and have the hardware only run software signed by me. not its much harder for anyone to hack my server.

the problem is if the company who makes your computer has the power to decide what you can run on it. for example the xbox (ignoring cracks/hacks) will only run code signed by microsoft. that makes an xbox no good as a linux computer. if PCs were to start shipping that only ran MS signed software that would be bad for linux.

if linux moved to gpl3 its hardly going to effect what hardware microsoft ship, or push onto the manufactures (eg will sell you windows OEM cheaper if you only make trusted computers). if you dont like drm dont buy drm music/video and dont buy trusted hardware.

if tivo, or anyone else want to use linux on an embeded system does that matter? how many ubuntu users give a direct contribution back to linux?

what i do like in gpl3 is closing the loophole that lets you use linux build a web based system and not having to give back patches because you are not distributing the software.

---

