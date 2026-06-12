---
title: "How bad is &quot;Shellshock&quot;"
date: 2014-09-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Chelidze on 2014-09-25
I have a question and hopefully linux gurus can answer me, So people are telling me that newly discovered vulnerability in bash is a very serious thing, and can be a big hit to Linux name.

So is it really that bad ??

[article]("http://www.linux.com/news/enterprise/systems-management/789353-concern-over-bash-vulnerability-grows-as-exploit-reported-in-the-wild")

Thank you in advance

---

### Post by Michael_McKenney on 2014-09-25
Very bad, if it can allow others to take over your computer.

---

### Post by Warren Hill on 2014-09-25
If you are running 10.04, 12.04 or 14.04 it looks like it's been fixed already. There is a Ubuntu Security Notice [here]("http://www.ubuntu.com/usn/usn-2362-1/"). To fix from the command line (desktop or server)

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Or the GUI way on a desktop. Run the Update manager, check for updates and update.

---

### Post by Chelidze on 2014-09-25
> **Warren Hill said:**
> If you are running 10.04, 12.04 or 14.04 it looks like it's been fixed already. There is a Ubuntu Security Notice [here]("http://www.ubuntu.com/usn/usn-2362-1/"). To fix from the command line (desktop or server)

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Or the GUI way on a desktop. Run the Update manager, check for updates and update.

Hm interesting but as I understand that fix is only a tee spoon in the ocean, because of the fragmentation.
If not is the media blowing it way out of the proportion ??

---

### Post by QIII on 2014-09-25
The media is over-blowing it to the point of missing some really practical realities, I think.

One simple reality is that if a lid is not put on it quickly, the idea that Linux is not subject to self replicating infection somewhat along the lines of viruses in Windows is at an end.

Persistent worms moving from infected machines to others becomes a very real possibility.  This is a bit of an "I told you so" moment for me, as I have been preaching for years that our arrogance and hubris might one day catch up to us.

However, most of this is theoretical right now -- it may be that the vulnerability will be patched quickly enough that only the sluggards who can't be bothered to keep their systems up to date will even see this by the time anyone figures out both a vector and a payload.

Between Shellshock and Heartbleed, I think anyone who says Linux is somehow "safe" is operating outside of reality.  I will say again, as always:  We need to be every bit as vigilent as Windows users in our security practices.

---

### Post by Irihapeti on 2014-09-25
It's the media's job to overblow things.

Anyone remember the 2008 openssl vulnerability? It was meant to mean the end of Debian, according to some. Last time I checked, Debian was still very much alive and well.


But we can do ourselves a huge favour by not repeating the nonsense about open source being more secure because "thousands of pairs of eyes are on the code". It's hasn't stopped vulnerabilities existing for years before being discovered.

---

### Post by d-cosner on 2014-09-25
I have always believed that every OS has vulnerabilities. In the end only the user can see to it that their system remains secure.

---

### Post by Chelidze on 2014-09-25
> **Irihapeti said:**
> It's the media's job to overblow things.

Anyone remember the 2008 openssl vulnerability? It was meant to mean the end of Debian, according to some. Last time I checked, Debian was still very much alive and well.


But we can do ourselves a huge favour by not repeating the nonsense about open source being more secure because "thousands of pairs of eyes are on the code". It's hasn't stopped vulnerabilities existing for years before being discovered.

It sound horrible to say the least, however I do not understand one thing back when "heartbeat" was the problem the community was really on their toes but on this issue they are being really quite, so I do not understand the issue what I can tell sounds really bad but the community is not very vocal at this point so based on that, does it means it's not as bad as pc world and other half informed websites saying it is ??

> **d-cosner said:**
> I have always believed that every OS has vulnerabilities. In the end only the user can see to it that their system remains secure.

I totally agree with you if something execute code it can be hacked but it does not sound too good to ask linux users get AV protections and other fun stuff :(

---

### Post by Warren Hill on 2014-09-25
> **d-cosner said:**
> In the end only the user can see to it that their system remains secure.

To be fair can they? If you are using an open source platform then you can examine the code but very few of us have the experience to do that.  I may and I have friends who can but I don't represent the majority.  If you are using a closed source system you are reliant on the actions of one particular company.

---

### Post by NoBugs! on 2014-09-25
From what I understand, it is a bad vulnerability if you use the ancient CGI web system, or anything else that lets untrusted input into bash?

---

### Post by philinux on 2014-09-26
[http://m.bbc.co.uk/news/technology-29375636](http://m.bbc.co.uk/news/technology-29375636)

BBC ran it too.

---

### Post by mörgæs on 2014-09-26
Yes, open source is generally safer than closed source because fixes are released and distributed quickly. Shellshock is a good example of that. We don't see known holes standing open for weeks / months as is sometimes the case for closed source.

The main problem is embedded Linux systems running in (old) routers, firewalls and other network equipment which are not maintained by the vendors.

---

### Post by christopher9 on 2014-09-26
and servers, routers, and applications sitting out there with default passwords.....

---

### Post by Mike_Walsh on 2014-09-27
Morning, all.

I've just been informed about this earlier this morning by a friend, who read about it in the Daily Mail. The friend in question has been considering getting me to change him over from Vista to Ubuntu, and of course, he's rather alarmed by this:-

[https://www.getsafeonline.org/news/severe-bug-warning-for-non-windows-computers-devices/](https://www.getsafeonline.org/news/severe-bug-warning-for-non-windows-computers-devices/)

Despite this only being announced very recently (apparently Wednesday mid-afternoon), the media appears to be jumping on the 'doom & gloom' bandwagon with enormous relish, just like they did over the 'HeartBleed' bug.

Just out of curiosity, what are other people's thoughts on this one.....and what damage can this REALLY potentially cause? According to this next link, the potential for this vulnerability has been lying dormant within Bash for the last 25 years:-

[http://www.troyhunt.com/2014/09/everything-you-need-to-know-about.html](http://www.troyhunt.com/2014/09/everything-you-need-to-know-about.html)

Comments?


Regards,

Mike.

---

### Post by Irihapeti on 2014-09-27
Threads merged.

---

### Post by Bucky Ball on 2014-09-27
*Thread moved to **Recurring Discussions**.*

Apparently ton of threads about this. No-one has followed the Ubuntu link on the [URL="https://www.getsafeonline.org/news/s...uters-devices/"]link in Mike Walsh's last post, #14???
[/URL]
> In general, a standard system update will make all the necessary changes.

About that simple. Keep your machine updated and upgraded. 

Consider this FUD, and if you don't know what that is, please check [HERE.]("https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt")

---

### Post by Elfy on 2014-09-27
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by The Cog on 2014-09-27
Ubuntu has had at least two updates for bash released in the last few days. That's pretty impressively quick to my mind.

Anyone who is running an un-patched system that is also running a CGI-based web server may be publicly vulnerable, and there are already a lot of them forming a botnet out there. Although to be fair, it's nothing like as bad as running XP.

I think there is a lot of noise about this because:
    It is unusual to find a widespread vulnerability like this in linux and *nix - it has novelty value.
    There really is a possibility that a lot of embedded un-maintained systems like printers, routers, TVs might be vulnerable.
    Commercial competitors may be encouraging as much noise and fud as they can.

---

### Post by Cliff_Simonds on 2014-09-27
From [Softpedia]("http://news.softpedia.com/news/TV-Stations-Cover-News-About-Shellshock-Bug-Flounder-Big-Time-460198.shtml#sgal_0") TV news anchors BASHing "LINECKS" and MACS. :p:p I saw this and I'm still laughing... just tickels me pink. What's next "The virus know as Windows Power Shell"? HA HA HA

---

### Post by Bucky Ball on 2014-09-28
> **Cliff_Simonds said:**
>  What's next "The virus know as Windows Power Shell"? HA HA HA

No, possibly what's next is the green slime that will devour the universe, and all other universes we humans haven't discovered yet also ...

---

