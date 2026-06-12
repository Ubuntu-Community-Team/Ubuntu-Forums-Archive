---
title: "I know why the Clippy board sings..."
date: 2006-07-12
forum: The Cafe
---

### Post by aysiu on 2006-07-12
I've often heard it said here that people don't like Windows because it treats its users like idiots.

Well, I spent some time last night with some wonderful people. They're moral people, fun people, and intelligent people. When it comes to computers, though, they're idiots. Unfortunately, there are some problems that go beyond even the power of Clippy or the search doggy (not Beagle/Kerry--the other one).

When you don't know you need a USB cord to download pictures from your camera, even Windows' "What do you want to do?" dialogues won't help you.

I'd almost forgotten how much a pain drivers were. They said their internet connection wasn't working. They'd called Comcast and gotten the Comcast CD. They even tried to use the D-Link router CD to fix things. To no avail, unfortunately. My wife and I had to hunt around to see what the problem was.

The *winipcfg* command didn't work, which prompted my wife to say, "Maybe this isn't Windows XP...?" (The computer had a Windows classic theme--not Luna or the Silver one.) But then she thought again and said, "No, I used the *winipcfg* command even in college on Windows 98." We knew something else had to be wrong. We dug around the Control Panel trying to remember how Windows did stuff with the internet (my wife uses OS X; I use Ubuntu). The Internet Connection wizard certainly didn't help us. Eventually, we found that device manager thing with all the yellow question marks.

Ah, the yellow question mark. My old buddy. It quickly reminded me why I love editing configuration files.

The people we were trying to help out had no idea where the driver CD was. They didn't even know what a driver CD was, so my wife and I ended up digging through their things to find Dell's restore disks. There were four restore disks. Three appeared to be driver CDs, and the descriptions on the CDs themselves weren't very helpful.

So I tried having Windows search for the driver on each CD. It couldn't come up with anything and wanted to find a driver from the internet. Uh... I'm not able to get on the internet--that's why I'm looking for the driver! Argh!

After a while, I gave up.

My wife took over. She looked through each CD, looking at the descriptions for each driver. Four of the drivers' descriptions looked promising, but since all we saw in the device manager was a big yellow question mark, we had no idea which driver to use. So she just double-clicked and trialed and errored until she found the driver that "worked." She still had to manually go in and select the driver.

Finally, though, it worked, and everyone was happy. Of course, our amazing-in-many-other-ways-but-computer-illiterate friends also needed her help setting up iTunes and their printer. My wife had to defragment their computer. *Sigh*.

It did make me think... despite the fact they'd have never have figured out the yellow question mark stuff by themselves... maybe they wouldn't mind Clippy popping up and saying, "It looks as if you're trying to type a letter. Do you want help with that?"

P.S. They were going to take it to some computer store to get the computer "repaired." Instead, we got a lovely homecooked dinner. My wife and I had to work for our meal...

---

### Post by bruce89 on 2006-07-12
> **aysiu said:**
> P.S. They were going to take it to some computer store to get the computer "repaired." Instead, we got a lovely homecooked dinner. My wife and I had to work for our meal...

That's how they make so much money, becuase Windows "breaks" (pun intended) all the time, and has lots of quirks, such as the one that you had to deal with.  
Windows needs 3rd party drivers, which can be rubbish, whereas Linux either supports hardware or not.

I quite like the doggy actually, my brother wonders who mentioned putting it in the search engine.  It is actually a remnant of MS Bob.

---

### Post by aysiu on 2006-07-12
At least the doggy's cute. She/he does get in the way of efficient searching, though--at least for me.

---

### Post by mcduck on 2006-07-12
> **bruce89 said:**
> 
I quite like the doggy actually, my brother wonders who mentioned putting it in the search engine.  It is actually a remnant of MS Bob.
For those who don't know Bob, it's a desktop enviroment for win3.11 and 95 that MS came up with when trying to make Windows more suitable for beginners..

Here's some screenshots: [http://toastytech.com/guis/bob.html]("http://toastytech.com/guis/bob.html")

---

### Post by aysiu on 2006-07-12
By the way, in case I have to troubleshoot something like this again in the future... is there any way to know, short of ripping open the computer, what kind of driver you need if you do see the yellow question mark?

---

### Post by Metacarpal on 2006-07-12
> **aysiu said:**
> By the way, in case I have to troubleshoot something like this again in the future... is there any way to know, short of ripping open the computer, what kind of driver you need if you do see the yellow question mark?

Personally, in those cases I usually look up the computer's model number online to get a list of components.  Which, ya know, doesn't help if you can't get online.  Nor in the case of custom-built PCs that aren't from one of the major wholesale-bad-parts-in-a-box companies (*cough*dell*cough*)...

---

### Post by angkor on 2006-07-12
I had a similar experience settings up a winXP box for my sister-in-law last weekend. Besides the amount of time installing (quite fast), downloading ( (no sp2 on the cd...*sigh*) and configuring stuff I also met the yellow question marks. 

I felt a strange sense of connection with all of those people who come to this forum to complain about how difficult Ubuntu is. I just don't really know what I'm doing on a windows machine. Since I only have experience with Win98 (a couple of years back) I just 'trial-and-error' stuff until it works. 

After I get the job done people look at me in amazement and say: "You should start doing something with computers for a living, you're sooo good at it..." I just smile and think "No I'm not!"

---

### Post by mcduck on 2006-07-12
> **aysiu said:**
> By the way, in case I have to troubleshoot something like this again in the future... is there any way to know, short of ripping open the computer, what kind of driver you need if you do see the yellow question mark?
I usually install the free version of Everest to check what components the computer has. I carry it around on USB memory, with free Kerio firewall, Avast antivirus, Firefox, Thunderbird, VLC and some other great and useful free (at least as in beer) apps that I usually install for people I'm helping..

Sadly, Everest is one of those programs that once were free, and now are not. But I stell think using the trial version is easier and faster than finding out the model number and spending some time with Google trying to find what parts are used.. Besides, if the machine isn't factory built there isn't even that option.

Anyway, here's a link for Everest: [http://www.lavalys.com/products/overview.php?pid=3&lang=en]("http://www.lavalys.com/products/overview.php?pid=3&lang=en")

If anybody knows a free app like this, I'd e very interested..

---

### Post by aysiu on 2006-07-12
Thanks for the Everest link. I'll look into it.

---

### Post by Polygon on 2006-07-12
the yellow question marks means that the drivers are not functional... obviously. Usually if you click the expand arrows it will tell you what kind of hardware it is, but if its too vague you can try going to the start menu (bottom left) and then going to run, then typing in "msinfo32.exe"

that program is suppost to give you a more detailed description on what hardware you have, although im not on windows to try it at the moment

---

### Post by aysiu on 2006-07-12
Polygon, thanks. Clicking on the expanded arrows didn't give me anything, but I'll keep *msinfo32.exe* in mind.

---

### Post by Polygon on 2006-07-12
also with some googling, i found a program called "aida32" which got discontinued because the developers went over to lavalys to make that everist program someone was talking about earlier in this topic.

im gonna go install it and see what it does real fast, hold on.

EDIT: oooo very nice program. I think this is what you need, well partially. This program does a nice job of telling you what hardware you have in your computer and stuff. Im gonna keep this program in mind.

But, to find the drivers you need, well thats a different story. My suggestion is to hop on a computer that has a internet connection and search "drivers for (whatever piece of hardware)" and see if you cant find a match, then try to find the driver on those infernal cd's... lol (you can generate a report of the computer by pressing the button next to the minimize/maximize/close buttons, and it will save as a html file so you can transfer it to a computer with a working net connection)



anyway, to download the aida32 program, go here: [http://www.majorgeeks.com/download181.html](http://www.majorgeeks.com/download181.html), and press one of the links with flags to start the download

---

### Post by djsroknrol on 2006-07-12
mcduck...when I was booting MS regularly, I was using a program called Belarc advisor to check things on my rig and other peoples...check it out, it works well...

---

### Post by mcduck on 2006-07-12
> **djsroknrol said:**
> mcduck...when I was booting MS regularly, I was using a program called Belarc advisor to check things on my rig and other peoples...check it out, it works well...
Thanks, I'll give that one a try next time I'm fixing somebody's machine :)

---

### Post by SonicSteve on 2006-07-14
Hi guys,
I've been a windows user for years. Other threads have said about O/S's that easy is simply what you get used to. I know many people just like the ones described at the beginning of this thread. I often take for granted the computer knowledge that I have. Most of my knowledge is windows based. I'm slowly getting used to Ubuntu and linux. 

BTY winipcfg was removed from WinXp The "repair" option under the context menu of each adapter was supposed to idiot proof the process. I like the winipcfg commmand. You can add it back by copying the file that runs the command and putting it in system32. 
The command line can still run the ipconfig command though.

---

### Post by Stormy Eyes on 2006-07-14
The people you describe, **aysiu**, are *welcome* to keep using Windows if it makes them happy. Me, I'll stick with Linux and Mac. Bollocks to Microsoft!

---

### Post by Koori23 on 2006-07-14
> **angkor said:**
> I had a similar experience settings up a winXP box for my sister-in-law last weekend. Besides the amount of time installing (quite fast), downloading ( (no sp2 on the cd...*sigh*) and configuring stuff I also met the yellow question marks. 

I felt a strange sense of connection with all of those people who come to this forum to complain about how difficult Ubuntu is. I just don't really know what I'm doing on a windows machine. Since I only have experience with Win98 (a couple of years back) I just 'trial-and-error' stuff until it works. 

After I get the job done people look at me in amazement and say: "You should start doing something with computers for a living, you're sooo good at it..." I just smile and think "No I'm not!"

I know how that goes.. I think the difference between "us" and the novice user is the fact that we're not afraid to click on stuff. When a screen comes up with two options "OK" and "CANCEL" a novice don't quite know which one to pick. Truth is, I don't either most of the time. I just choose one, see how that works out. It's not that I'm smarter or anything.. I just figure stuff out one step at a time.. Of course I've made mistakes, but with Windows, you tend to see the same errors over and over again and it's automatic. Man, I can't tell you how many Windows machines I've screwed up because I was just guessing. If you screw up enough, you tend to figure out  what not to do. I guess I'm just not afraid to screw up.

---

