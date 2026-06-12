---
title: "Monitor Setup Question"
date: 2006-08-03
forum: The Cafe
---

### Post by souled on 2006-08-03
I'm thinking about upgrading my monitor setup (currently a 17" CRT :???: ). I am thinking about either 2 19" or 2 19" widescreens. What are the pros and cons of both setups? I don't think I can go any bigger than 19" because of cost, so please don't say something along the lines of 'Dell 30" FTW!!!' Please give me some insight; this is a big step for me (considering I have to pay for this myself (I'm only 16)). Thanks a lot.

---

### Post by Mathiasdm on 2006-08-03
Make sure your graphics card supports it!
Sadly, mine doesn't :mad:

---

### Post by ylixir on 2006-08-03
i recently bought a widescreen 19" lcd.  i like it a lot, the wider screen really makes more room for me to work.  even though the screen is technically the same size, it just seems like i can lay out more stuff on it because of the width.

it's not hassle free though.  just getting the thing to work was a major headache.  for example, in linux i have to manually specify the modeline because my video driver doesn't have a default mode for it's resolution that works.  and the only video driver i've been able to get working in freebsd is vesa, and it doesn't look like there are any vesa supported widescreen resolutions.  so freebsd is essentially useless to me at the moment.  but it's simple to google "modeline generator" and paste the output into xorg.conf.  well worth the extra space for the trouble of getting it running i think.  now if ati would only release some freebsd drivers...

---

### Post by mozetti on 2006-08-03
I just picked up a 19" widescreen LCD, too. It's a [Hanns-G from TigerDirect for $180US](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1828823&CatId=0).

It's a beauty, and I agree with ylixir about how it seems "bigger." I didn't have any trouble getting it to work, but like ylixir, when I reconfigured Xserver (i think the command was "dpkg-reconfigure xserver-xorg") it didn't have a modeline for the ideal resolution (1440x900@60Hz). But, it was easy enough to use the Advanced setup to specify the resolution and freqency ranges.

So, if you're looking for a great LCD (5ms response, widescreen, 19", DVI) with a 3-year warranty at a great price then check this one out (feedback on tigerdirect is great, too).

Ok, so I realize I sound like a salesman, but I'm pretty happy wit h this monitor.

---

### Post by mozetti on 2006-08-03
**EDIT** damn double-posts

---

### Post by beniwtv on 2006-08-03
I have an Acer 19" widescreen. It's amazing :mrgreen: Need I say more?

I didn't have problems getting it to work, I just changed X.org from 1024x768 to 1440x900. That's all. Hope in Edgy we will have a graphical tool for this 8)

---

### Post by souled on 2006-08-03
Thanks for the replies. What I really want to know is about dual widescreen setups. I've searched around Google a little bit, and I've seen people say go single widescreen over two monitors, but what about dual widescreens over two non-widescreens? Surely if one widescreen is better than two non-widescreens, than two widescreens has got  to be awesome, no? Although there is the problem that it might be too wide. Is going dual widescreens really worth the investment? Keep the input coming! Thanks.

---

### Post by John.Michael.Kane on 2006-08-03
You can search the forums for twin view or dual monitors. also your not being very specific about what you want to know. if space is an issue then get one widescreen as large as your budget,and space will allow for. also you really should list what you will be doing with the lcd's as speed does come into play ranging from low 5ms and up. also listing your system spec's would help too.

---

### Post by schurtek on 2006-08-03
Dude... this is a wise move... 19" in my experience is the canopy top for desktop displays, as anything bigger becomes to cumbersome on your desk, unless you can dosh out on a plasma 42". 

Firstly ensure that your display card supports the max resolution and refresh rate of the monitor. I setup a four way 19" display computer in a recording studio once... the best resolution I found on a 19" was 1600x1200... on my 17" I run 1280x1024 and on my 15" I run 1024x768. 

I can not understand why some people will go out and buy a 17" display and run it on a low resolution. It look crappy and you are throwing away all that precious desktop space...

Well that's my advice...

---

### Post by souled on 2006-08-03
Well, first of all, I'm planning to build a completely new system. Some components I'm looking at include the Core 2 Extreme and possibly a 7950 GX2. I'm pretty sure that setup will handle dual monitors (be it widescreen or not) (can you see why I don't have much to spend on the monitors? :D ) I plan to use this machine for movies (no other dvd player in my room), gaming, and general multi-tasking. I like to play around with Photoshop (which I hear is great on dual screens), and I'm going to be going off to college in 2007 if that makes any difference.

Some information I would like to know is how much an advantage would dual widescreens be over two non-ws? The ws would be great for watching movies on (which I do frequently), but what about gaming? Or maybe I should look into one ws and one non? That way I could use the ws for movies and such and then have the second monitor for other apps. I'm starting to question what the point of having two ws monitors (or is there none?) 

On a side note... I'm posting from work, and I just hooked up a second monitor to my laptop. I've had a 20" (or so) CRT sitting in my cube for the past 7 weeks and I've never used it! I can't believe how much better it is with two monitors! It's ashame I'll be leaving next week (only an intern).

Well, keep the posts coming. I appreciate all of the feedback.

Did I use enough parenthetical statements? lol
Err... sorry for the long post... I didn't realize I rambled on so much.

---

### Post by schurtek on 2006-08-03
If the game doesn't support widescreen, then it will have two black edges, kinda like when you watch wide screen movies on your monitor and you get the letter box effect... just on it's side now... when the game does support widescreen (which then it will probably support dual screen.... then you will have the most awesome gaming experience ever...

---

### Post by souled on 2006-08-04
If a game supports widescreen, will it be stretched out looking?

Now that I think about it, I might seriously be considering one ws and one non-ws. I can play games on the ws (if they support it), watch movies, and do stuff that just might be better done on a ws. On the non-ws I can just do general multi-tasking. 

I think i'm going to go dual for sure so I can do stuff while using full-screen applications. The question is, what setup should I go for...

Does anyone have a ws and non-ws setup? I realize that they won't exactly line up, but I don't really think that would pose a problem. This would save desk space, and it would give me a little more realty with the non-ws. Any input on this idea?

---

### Post by ylixir on 2006-08-05
the games i have that support widescreen aren't stretched out looking.  actually it's really nice on most of them to see that extra little bit of space on the sides.  but it's not THAT nice for gaming.  it's a nice perk, but it's not nice enough for me to say it's definitely worth going widescreen for.  i'm just a fan of widescreen for the more efficient use of screen real estate for desktop/workstation purposes.

---

### Post by thexaspect on 2006-08-05
sorry ylixir, but I've gotta say, running games on my widescreen is just incredible. granted, i only play world of warcraft, but if it's any indication, the difference in the amount of the world i can see at one time has saved my rear on more than one occasion. the great thing, with a decent enough graphics card(i've got dual 7600GT's in SLi), you can watch a movie on the other monitor at the same time, which is really nice with a pair of dell 2007FPW's =). btw souled, when I used to run windows on my gaming box with a widescreen, i didnt run into any modern games that didnt support widescreen format as long as you had the graphics hardware to support it. halflife2, doom3, world of warcraft, guild wars, etc. good luck with the new box =)

---

