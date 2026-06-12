---
title: "Damaged video card? What should I do?"
date: 2006-07-14
forum: The Cafe
---

### Post by PatrickMay16 on 2006-07-14
Hello everyone.

Recently I got a new video card (NVIDIA GeForce 6200), and it works fine for the most part, and stable; I can play games and stuff that used 3D accelleration fine. There is a problem though; sometimes during video playback, I get strange red and blue colour artifacts appearing over the image. I took some screenshots of it happening:

[http://img472.imageshack.us/img472/2513/colorz4na.png](http://img472.imageshack.us/img472/2513/colorz4na.png)
[http://img115.imageshack.us/img115/3721/colorjunk4nh.png](http://img115.imageshack.us/img115/3721/colorjunk4nh.png)

Sometimes this doesn't happen at all, other times it happens a little bit, and other times a lot.

I use NVIDIA's official linux drivers. But after some testing I found that this problem also happens when using the open source "nv" driver, or Windows 2000.
Plus, I tried mplayer with some different video output methods (sdl, x11, gl) and the problem continued to occur.

I checked the temperature the graphics card was running at, and it said 55 degrees celcius. That doesn't seem to be too hot.

I think it's a hardware problem, but I want to know what you guys think first. Do you think it is indeed a hardware problem, or could it be that some BIOS setting isn't correct or something?
I've only had the card a couple of weeks, so the place I bought it from will probably replace it.

So, what do you think?

---

### Post by ComplexNumber on 2006-07-14
55 degrees is quite high, and isn't that far off the usual threshold (assuming you have a pentium 4). i have a pentium 4, and when it starts getting to 60+, it starts going slightly funny. i had a problem recently where the system froze. everytime i rebooted, it wouldn't boot back. i had to switch the PC for a while, then it was ok.
having said that, pentium 4's shouldn't really do that because it has ways of dealing with it (ie going into reduced clock mode (or something like that)). 

i honestly don't think its a hardware problem. i think its a temperature problem. switch your pc off and wait a few minutes for it to cool down. also, try to minimise the number of cpu intensive operations at that time. you may notice that it only starts going funny when it reaches a certain temperature.

---

### Post by PatrickMay16 on 2006-07-14
Thanks for the reply, Complexnumber.

By the look of it, I think you misunderstood me; I wasn't talking about the CPU temperature, I was talking about the GPU temperature:

[http://img99.imageshack.us/img99/3655/nvidiasettinghd5.png](http://img99.imageshack.us/img99/3655/nvidiasettinghd5.png)

In nvidia-settings's little meter thing, 55 degrees seems to be low down in the green area, so I assumed that it was OK.

By the way, my CPU is pretty well cooled; plus I have AMD's cool'n'quiet technology enabled so it's throttled down during low usage. I notice sometimes on hot days its fan will spin faster during high CPU load, but not very often. 
So the CPU is probably not the problem... but I dunno.
But anyway, like you've suggested I'll keep the computer turned off for a while to cool it down, then see how things go.

Thanks again.

---

### Post by Engnome on 2006-07-14
omg 145 C threshold O.O That is a lot compared to the 55 C you have...

BTW thx for the anime tip :)

---

### Post by Polygon on 2006-07-14
im pretty sure that you would want your gpu to be a low of a temperature as possible, and even though 145 degrees C is the treshold, i think that is only the number before your GPU explodes rather then getting the best performace

Are the wires inside your computer organized as best they can? having a very messy case can interfere with cooling and the airflow of the fans, so if its a mess, i would take some twistyties or those plastic wire holder things and try to organize the wires as best you can.

and also try taking a straw and blowing the dust out of your computer, especially the fans.

---

### Post by ComplexNumber on 2006-07-14
> I wasn't talking about the CPU temperature, I was talking about the GPU temperature oh, i see. well, do you notice any correlation between the temperature of the CPU/GPU and when everything starts going funny? what CPU have you got?
when video cards act as they do in those images, its a temperature problem...guaranteed.
le me know how you get on.

---

### Post by PatrickMay16 on 2006-07-14
Thanks for the replies, everyone.

For about an hour I had my computer turned off (with the power switched off at the wall as well, to make sure), and my window wide open with my deskfan blowing the night air into my room. I turned my computer on and logged in as quickly as I could, and started playing a video. The problem occurred right away. I monitored the temperature of the GPU while this was happening, and it was around 37/38 degrees celcius. That was a couple of minutes ago now, and the temperature has risen to 46 degrees.

---

### Post by RJARRRPCGP on 2006-07-14
> **ComplexNumber said:**
> 55 degrees is quite high, and isn't that far off the usual threshold (assuming you have a pentium 4). i have a pentium 4, and when it starts getting to 60+, it starts going slightly funny. 

I wouldn't worry until it gets to around 70 C (160 F) or around 65 C (around 150 F) It usually won't be unstable until the mentioned above temperatures.

If it was unstable related to temperature, it probably skyrocketed to at least around 65 C. When this occurs, especially when OC'ing, a lower than actual temperature may be reported, it may only say 55 C (131 F) when it actually went to 70 C! (160 F)

Chances are that this occured when running Prime95 (Windows) or mprime. (Linux) 

If you were running any of the above, if the processor was overheating, that may cause the following symptom:

You got a low processor temperature reading, but the system suddenly hard locked. If you got a hard lock up, it may appear that the temperature stabilized. That's because it actually stopped updating!

---

### Post by ComplexNumber on 2006-07-14
> **PatrickMay16 said:**
> Thanks for the replies, everyone.

For about an hour I had my computer turned off (with the power switched off at the wall as well, to make sure), and my window wide open with my deskfan blowing the night air into my room. I turned my computer on and logged in as quickly as I could, and started playing a video. The problem occurred right away. I monitored the temperature of the GPU while this was happening, and it was around 37/38 degrees celcius. That was a couple of minutes ago now, and the temperature has risen to 46 degrees.
seems rather odd that it should start playing up right away :confused:. and you mention that your fan is ok on the CPU (what about the fan on the GPU?). its almost as if its been 'sensitised' to the temperature.




> **RJARRRPCGP said:**
> I wouldn't worry until it gets to around 70 C (160 F) or around 65 C (around 150 F) It usually won't be unstable until the mentioned above temperatures.

If it was unstable related to temperature, it probably skyrocketed to at least around 65 C. When this occurs, especially when OC'ing, a lower than actual temperature may be reported, it may only say 55 C (131 F) when it actually went to 70 C! (160 F)

Chances are that this occured when running Prime95 (Windows) or mprime. (Linux) 

If you were running any of the above, if the processor was overheating, that may cause these symptoms:

You got a low processor temperature reading, but the system suddenly hard locked. If you got a hard lock up, it may appear that the temperature stabilized, but it actually stopped updating!
yes, thats sounds about right. interesting about the hard lock.

---

### Post by PatrickMay16 on 2006-07-14
> **ComplexNumber said:**
> seems rather odd that it should start playing up right away :confused:. and you mention that your fan is ok on the CPU (what about the fan on the GPU?). its almost as if its been 'sensitised' to the temperature.

There's no fan on the graphics card, just a heatsink. Not identical, but very similar to this:
[img]http://img212.imageshack.us/img212/9099/gcdxfx62008oh.jpg[/img]

---

### Post by ComplexNumber on 2006-07-14
oh, i see. i thought it may have had a fan on. some of the higher end ones do.
it seems like we need more clues, but because i'm not an expert in this area, i can only go by what i know.....so i also don't know what other clues to ask for. 
video playback is hugely CPU/GPU intensive....perhaps more than anything (except gaming) because of the amount of processes involved. can i assume that its ok for games, but not ok for video playback?

---

### Post by PatrickMay16 on 2006-07-14
> **ComplexNumber said:**
> can i assume that its ok for games, but not ok for video playback?
Yep. I'm able to play Unreal or the UT2003 demo or use Mupen64 just fine; no problems at all there.

---

### Post by ComplexNumber on 2006-07-14
> **PatrickMay16 said:**
> Yep. I'm able to play Unreal or the UT2003 demo or use Mupen64 just fine; no problems at all there.
seems curious. maybe video playback is more intensive than even gaming. this would perhaps mean that it does have something to do with the temperature being a factor. i'm out of my league now, because i really can't think what it could be....but i don't think you have a faulty video card or anything. it seems strange how the temperature rises quite sharply when you use video playback. i'm wondering if there is some conenction between the video card behaviour and the speed of increase in the temeperature. maybe something to do with the codecs.
hopefully someone whos had the same problem or who is more knowledgable can point you in the right direction.

---

### Post by Stew2 on 2006-07-15
Just out of curiosity, does it do this with other movies or just the avi's? If it works fine in games with no artifacting or locking up I would almost lean towards problems with the codecs or the source avi's. Same errors in the same places every time or do the errors jump around randomly? It also does the same thing in Windows with current video card drivers? Almost sounds like corrupted files. Usually a video card going bad will be much more dramatic such as major artifacting, or locking up. I don't think heat is an issue here as your temps aren't that high. Does it do it with mpegs and DVD's too? You could try returning it if it is still under warranty and seeing if another card solves the problem. Most places dont have a problem with hardware returns if you tell them its not working right :). Let us know how you make out.

Regards,
Stew2

---

### Post by PatrickMay16 on 2006-07-16
> **Stew2 said:**
> Just out of curiosity, does it do this with other movies or just the avi's? If it works fine in games with no artifacting or locking up I would almost lean towards problems with the codecs or the source avi's. Same errors in the same places every time or do the errors jump around randomly? It also does the same thing in Windows with current video card drivers? Almost sounds like corrupted files. Usually a video card going bad will be much more dramatic such as major artifacting, or locking up. I don't think heat is an issue here as your temps aren't that high. Does it do it with mpegs and DVD's too? You could try returning it if it is still under warranty and seeing if another card solves the problem. Most places dont have a problem with hardware returns if you tell them its not working right :). Let us know how you make out.

Regards,
Stew2

Yo, man.

First I'd just like to say thanks for the replies, everyone.

It does this with other movies; I've tested quite a few different ones, and it happens with them too. So far it's happened in all the different videos I tried playing it with at some point. 
I'm not sure if it appears exactly the same or slightly different with each time that it does it, but for some videos it appears in the same general area; like where there are some darker shades of colour or something.
But definitely I can play a video and the problem does not happen at all, and then later I could play the same video and that time around the problem does happen.

---

### Post by Stew2 on 2006-07-16
So it happens with other video formats as well? I think that I would be inclined to return the card for a new one and see if that does the trick. Also double check to be sure it is well seated in its slot. If it is happening in both Ubuntu and Windows I think the drivers and codecs are alright but the card might be bad. Hope this helps! :) 

Regards,
Stew2

---

### Post by ComplexNumber on 2006-07-16
> But definitely I can play a video and the problem does not happen at all, and then later I could play the same video and that time around the problem does happen. did you notice any difference (any at all) about the system between when the videos played ok and when they didn't? thats obviously going to be the biggest clue. maybe temperature can (possibly) be ruled out as a factor here. i assume there is  no other application running when you play videos. 
have you tried using anything other than mplayer?
the problem may be to do with the drivers or xorg. also, are you using xine as a backend?

---

### Post by PatrickMay16 on 2006-07-16
> **Stew2 said:**
> I think that I would be inclined to return the card for a new one and see if that does the trick. Also double check to be sure it is well seated in its slot. If it is happening in both Ubuntu and Windows I think the drivers and codecs are alright but the card might be bad. Hope this helps! :)

Thanks. I'll try taking it out, and putting it back in again firmly to see if this helps. If not, I'll send it back and get a different one.

> did you notice any difference (any at all) about the system between when the videos played ok and when they didn't?
Nope. Everything other than the video playback at that time is normal.
I've tried Windows Media player 6 on Windows, and totem-xine on linux other than mplayer. It happens with all of them.

> the problem may be to do with the drivers or xorg. also, are you using xine as a backend?
I'm using xine as a backend for video playing in totem, but I'm not sure about mplayer; how would I find out there?

---

### Post by ComplexNumber on 2006-07-16
>  I'm using xine as a backend for video playing in totem, but I'm not sure about mplayer; how would I find out there? to tell you the truth, i'm not entirely sure. 


i think i know what the problem is - you either need to upgrade(try this option first) or downgrade your nvidia drivers. this may give you hope:
[http://www.gsc-game.com/index.php?t=community&s=forums&s_game_type=fs&thm_page=1&thm_id=99&sec_id=1&offset=-60](http://www.gsc-game.com/index.php?t=community&s=forums&s_game_type=fs&thm_page=1&thm_id=99&sec_id=1&offset=-60)

---

### Post by PatrickMay16 on 2006-07-16
> **ComplexNumber said:**
> to tell you the truth, i'm not entirely sure. 


i think i know what the problem is - you either need to upgrade(try this option first) or downgrade your nvidia drivers. this may give you hope:
[http://www.gsc-game.com/index.php?t=community&s=forums&s_game_type=fs&thm_page=1&thm_id=99&sec_id=1&offset=-60](http://www.gsc-game.com/index.php?t=community&s=forums&s_game_type=fs&thm_page=1&thm_id=99&sec_id=1&offset=-60)
I just tried installing the newest driver in Windows, and the problem's still happening. 

Well, seems like all there is to do is to return and get a different one.
Thanks for all the help, everyone.

---

### Post by ComplexNumber on 2006-07-16
> **PatrickMay16 said:**
> I just tried installing the newest driver in Windows, and the problem's still happening. 

Well, seems like all there is to do is to return and get a different one.
Thanks for all the help, everyone.
darn it! i really thought that was the solution. considering you're getting the same behaviour in both windows and linux would suggest that its not a driver issue at all.
yes, i think you should take it back and see what the technical support have to say.

---

### Post by grim1234 on 2006-07-16
It sounds like your card is damaged but try this :

underclock the video card (use nvclock-gtk in nix or riva tune in windows), then try to play a video. If the problem stops when underclocked you've got a bad card for certain. 

As for the temperature below 60 is fine for an nvidia card as they run pretty hot.

---

### Post by Stew2 on 2006-07-16
> **PatrickMay16 said:**
> I just tried installing the newest driver in Windows, and the problem's still happening. 

Well, seems like all there is to do is to return and get a different one.
Thanks for all the help, everyone.

If you don't mind me asking, where did you buy it. I bought a video card at Future Shop once and couldn't get it to work on an old machine I had. While waiting in the returns line I was working on cooking up an elaborate excuse as to why the card did'nt work and the girl had already deposited my money back into my bank account before I had a chance to get any excuse out :D . Overpriced but a very good return policy! :D Hopefully you don't have to mail it somewhere and be without a computer until you get it back :( !

Regards,
Stew2

---

### Post by PatrickMay16 on 2006-07-16
> **Stew2 said:**
> If you don't mind me asking, where did you buy it. I bought a video card at Future Shop once and couldn't get it to work on an old machine I had. While waiting in the returns line I was working on cooking up an elaborate excuse as to why the card did'nt work and the girl had already deposited my money back into my bank account before I had a chance to get any excuse out :D . Overpriced but a very good return policy! :D Hopefully you don't have to mail it somewhere and be without a computer until you get it back :( !

Regards,
Stew2

I got it from [www.aria.co.uk](www.aria.co.uk). It's pretty good; I get all my computer hardware there, and I've been able to return stuff to them before without problems.
It'll have to be mailed back, but no problem; I've got a spare Radeon 9000 to use while waiting.

---

