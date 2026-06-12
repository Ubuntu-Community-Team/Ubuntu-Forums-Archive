---
title: "Record Player MP3 Megastation (Summer Project)"
date: 2012-03-31
forum: The Cafe
---

### Post by Hobomank on 2012-03-31
So I have an old record player cabinet with worn out( and quite  expensive to replace) needle, and the turntable has pretty much seen the end of its days, as it won't spin at all. it has has been serving as, pretty much, a  coffee table for a year. And I have an outdated hp pavillion xg834 and CRT monitor I bought  from yard sale which has basically been, well, useless. I don't use it. so instead of Sending them off to the landfill i'de like to make use of them.[ I read here about someone who used their  record cabinet as a mp3 Cabinet.]("http://hackaday.com/2011/09/07/broken-vintage-record-player-reborn-as-a-portable-mp3-cabinet/"), I'd like to do something similar.


[IMG]https://fbcdn-sphotos-a.akamaihd.net/hphotos-ak-ash3/s320x320/543748_417743328251225_100000466849330_1639240_635830756_n.jpg[/IMG]

Some things it will be able to do:

1. play nearly every audio codec known to man

2. wifi connectivity, with direct access to all music related sites and direct options for transmission :wink:

3.Phonograph underneath( I have  working record player, just not this one :) )

4. act as my home music server with a 1.5 terabyte external HD 

5. Owncloud...possibly

 However, I'm running into some issues on some things I want out of the system software wise:
1.Very Lightweight OS, this is an old computer so have I a need for speed :-P

2."Juke box" oriented GUI. I do not want it to look like desktop in any  way. more like a digital juke box, with options for home music folders  in the forefront)

3. capacity for touch-screen compatability. as I Plan on adding a touch screen overlay sometime in the future.

4. Access to sites within a browser that takes up the whole screen,  giving the illusion that the website is an application, intstead of a  browser.

So my question is this: Does a distro and web browser with these 4  prerequisites exist? or will it probably better suit my purpose to  construct these features from scratch in archlinux(or another highly  customizable distro ). If so can you guys give me some resources?

I'm fairly new at programming but i do have the capacity and will to learn.

And if you guys think this project is as cool as I do I'll keep you posted on my progress, I begin work on it tomorrow. :guitar:
If it werent for linux being so freakin awesome I wouldn't even attempt to do this.

---

### Post by Old_Grey_Wolf on 2012-03-31
I like the idea of reusing the cabinet; however, I think you need to check the specification for the HP Pavilion xg834. 

I don't think it will give you the storage (1.5 TB) or performance you desire. The HP Pavilion xg834 can only have a maximum of 512MB of memory; which, limits the GUI options that you can use on it. It also seems to have an IDE/ATA disk controller that may not support more than about 137GB (from a very brief browse on the Internet).

If I was going to spend the time to refurbish the cabinet, I wouldn't put a 6 to 10 year old computer it it that may not survive very long.

After spending days modifying the cabinet, applying new varnish, feeling good about my accomplishment, I wouldn't be happy if the old computer decided to die on me.

---

### Post by Hobomank on 2012-03-31
well even then that still more than enough memory for an mp3 cabinet. I've always found them to be a very sturdy computer, and whats more is I've seen them everywhere. too, Linux will make any old system wake up from the dead. It wont need much cpu because it will just be a big jukebox.

These computers have  history of "breaking down"?

---

### Post by SemiExpert on 2012-04-01
Not very energy efficient or silent.  Socket 370 motherboard?  CRT monitor?  I'd go for a fanless ARM approach.  Here's a few examples:  [http://trimslice.com/web/](http://trimslice.com/web/)[http://www.genesi-usa.com/products/efika](http://www.genesi-usa.com/products/efika)[http://www.raspberrypi.org/](http://www.raspberrypi.org/)Actually, if ever clears the hurdles, the Raspberry Pi is the most fascinating choice - and the cheapest.  The choices for x86 are probably safer, and if you don't need powerful graphics, there are plenty of dirt cheap mITX boards with Atom processors.  Newegg sold out on a sub-$40 mITX board with an E-350.  Cheap.

---

### Post by Old_Grey_Wolf on 2012-04-01
> **Hobomank said:**
> well even then that still more than enough memory for an mp3 cabinet. I've always found them to be a very sturdy computer, and whats more is I've seen them everywhere. too, Linux will make any old system wake up from the dead. It wont need much cpu because it will just be a big jukebox.

Your question seemed to be, "Does a distro and web browser with these 4 prerequisites exist?"

I was looking at your "wish list" and noticed the 1.5TB disk and the juke-box GUI you wanted with a touch screen. Then I looked for the HP Pavilion xg834 specs on-line. The OS isn't going to overcome the limitations of the hardware you have.

I was just suggesting that you may want to check the specs of the PC you have before spending a lot of time on the project. Your computer may have better spec than what I found during a brief search. You may decide that you need to use a different computer, or the necessary upgrades to the one you have isn't practical from a cost perspective.

I wasn't suggesting that Linux wouldn't work on it. What I was suggesting is that with the prerequisites you listed, that may exclude the hardware you have available; however, you need to investigate to know for sure. :)

> **Hobomank said:**
> These computers have  history of "breaking down"?

Actually, a similar computer I had was very reliable. It just became obsolete and expensive to maintain. It wasn't meant to run anything newer than Windows XP. The cost of keeping it woking was more than the cost of a new computer. :)

---

### Post by aeroflotsam on 2012-04-02
Good luck with your project..... The cabinet looks good and almost as if it might have been a Webcor or Silvertone Hi-Fi console.  As a kid in the 50's I worked part time in a radio and TV repair shop.  I wish I had some of those old cabinets we carted off to the dump back then.  Some of those radios dated to the early 20's and people out in the country were still sending them in for service.

I once built an entire ham radio station into a Magnavox cabinet and it looked really good.  Looks like you might have a classic steampunk project in the works... You'll always take a great deal more satisfaction from something you put together with your own hands than you would with some shiny "doo-dad" that the Wal-Mart merchant piggy tries to sell you.  If funds are available you might wanna think about a little newer computer to base your system on; if not then whip that old clatter box into shape and make it work!

Enjoy your project and post your results.

Cheers

---

### Post by winh8r on 2012-04-02
Take a look at Crunchbang Linux or Lubuntu for lightweight OS'es.

[http://lubuntu.net/about]("http://lubuntu.net/about")

and

[http://crunchbanglinux.org/wiki/about]("http://crunchbanglinux.org/wiki/about")


My only concern would be getting rid of the heat from in there, you are going to need a couple of fans on the cabinet somewhere to keep the air flowing through.

and this might be useful too:

[http://www.amazon.co.uk/Flexible-Foldable-Silent-Silicone-Keyboard]("http://www.amazon.co.uk/Flexible-Foldable-Silent-Silicone-Keyboard/dp/B000UMJFJU/ref=sr_1_2?ie=UTF8&qid=1333406945&sr=8-2")


It seems like you have the desire to make it work, so why not!!!


I would like to see some pics of it when you get it finished too!


Good Luck

---

