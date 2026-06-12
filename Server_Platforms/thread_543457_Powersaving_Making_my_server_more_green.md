---
title: "Powersaving: Making my server more green"
date: 2007-09-05
forum: Server Platforms
---

### Post by Gruelius on 2007-09-05
Hey all,
Last powerbill was $900 so im looking into powersaving, allways been putting it off :P. Anyway the server has:
AMD X2 3800+
1gb DDR2
Pioneer DVD RW
5 x 200GB IDE Disks (running in MD raid5 array)
1 x 40GB IDE disk

The server BARELY gets pushed on normal use. (Load average is .01 ish (( 19:22:33 up 25 days,  2:03,  1 user,  load average: 0.00, 0.01, 0.04
)) ). All it does is serve music, tv shows and act as a proxy and web server. I realise that if i start to shut it down or put it into standby these functions will not work, so i wil have to make a comprimise.

The raid array is only accessed when TV shows, Music and Download archives are accessed. The rest is done from the 40gb (Soon to be replaced with a 120gb raid1). 

I would like to set it up so the raid array spins down if that is the best option. I would also like to set a more aggressive cpu frequency slowing down thing ( At the moment all i have setup is cpufrequtils which slows my server down to 1ghz ).

Any other suggestions would be great!
Thanks
Julius

---

### Post by southernman on 2007-09-05
Holy crap! Was that for a year or just a month? ;)

Honestly, at that amount, turning your computers off completely won't really make much difference in your power bill. Surely your server can't be eating more than 20-25 bucks a month of power consumption

Allowing your drives to spin down will cost you more than it will save you in the long run... IMO at least. It's bad for their health.

You would be a good candidate for some type of wind or solar power. It may take a few years to see a ROI, but you will see a ROI for sure.

Completely off topic here but bare with me. If you use an electric water heater, you can save 20-25 or more a month by installing a timer or a simple 220V switch on it and turn it off prior to bed time, on after getting up, back off prior to leaving for work, and back on when returning (hence the timer suggestion). 25 bucks a month is what my family of 3 realized in savings by doing this.

---

### Post by Gruelius on 2007-09-05
its  per quarter and in $AU

i suppose i should look around the house then eh :P

---

### Post by ssam on 2007-09-05
get yourself a power monitor (like one of these [http://www.reuk.co.uk/Kill-a-Watt.htm](http://www.reuk.co.uk/Kill-a-Watt.htm) ) then you can figure out how much powersaving you get with various optimisations.

do you need a AMD X2 3800+, via epia systems use very liitle power. but may not be fast enough for heavy multimedia stuff.

put your root patition on a compactflash card, this will reduce how often the disks need to spin up.

---

### Post by HermanAB on 2007-09-05
Hmm, in Australia everything runs on electricity, so you'll find that your main power drains are water heating and air conditioning.  Wrap an extra layer of fibreglass around your heater, and insulate the hot water pipes as far as you can reach them.  

About the rest you probably cannot do much.  If you use airconditioning, then a couple of well placed awnings will bring that cost down.  You could also switch to fluorescent bulbs for the most used light fittings.  Changeing power settings on the server won't make much diff - compareable to one lightbulb.

---

### Post by Gruelius on 2007-09-05
You are correct in saying the X2 3800+ is a bit overkill. The cpu draws 45w when on standby tho and i wouldnt be ready to shell out more kudos for a epia system. THe grunt is used ocasionally when i need to transcode video otherwise it just sits there :p

Ill have a look at the other things. Since it wasnt summer the AC wouldnt have been used.

lightbulbs would also be another big thing.

I know this isnt server related but how would i go about getting S3 and hybernate to work? not for the machine in question but for the desktop in sig and another simillar machine.

---

### Post by Antonlacon on 2007-09-06
[http://linuxpowertop.org/](http://linuxpowertop.org/)

Lists the amount of times your cpu wakes up, and offers suggestions for lowering.

---

### Post by HermanAB on 2007-09-06
Hmm, buy two fluorescent bulbs and forget about the server...

---

### Post by southernman on 2007-09-06
If you the tinkering type (read: crafty with your hands), try this on for size. 

[http://www.eng.uwaterloo.ca/~gmilburn/ac/]("http://www.eng.uwaterloo.ca/~gmilburn/ac/")

Summer is about done here in good ole mississippi, but I've already got the core from an old freezer to build mine.

As for the light bulbs... Incadescent lighting is sooooo 20th century! It's only rumor, but I've heard the us gov is planning to ban them. Like they actually care!

---

### Post by netlogic on 2007-09-09
You aren't going to save that much money on **home** servers. I would concentrate on your making your desktop to suspend more. Making the server suspend would defeat the purpose of the server. Put intensive process jobs to your server, so your desktop can be more idle and save power. If you have many servers, you should get into virtualizing all your servers into one. CPU scaling will not save you that much on the server. Also, it isn't good idea to constantly suspend home servers' drives. Drives last more when it is constantly rotating and maintain the same cool temperature. Also, it is usually a drive only eats 3w to 5w each. You can also save 1 to 2w per hour if you yank out optical drives that aren't being used. The optical drives will consume energy even they aren't being used. The monitor eats the most energy compares to other hardwares. Make sure you switched to LCD from CRT. LCD monitor will pay for itself within 3 to 4yrs. I think you are better off focusing on the desktop and start using less machines. If this is a big issue, look into NSLU2 or other Linux embedded server options or start using an older machine (less processing power) with a newer power supply.

Energy consumptions of the computer as listing the highest in the listed order.
1. CRT monitor 80 watts
2. LCD 35 watts
3. processor varies a lot
4. optical drives 6w to 7w
5. drives 5w
6. various internal pc components (it is kind of impossible to measure).

If this energy consumption is getting on your nerves, replace your desktop with a laptop. That will save enough to see the differences in your bill. Also, invest on killawatt to see what really eats up your energy bill.

---

### Post by netlogic on 2007-09-13
I found some good information. I hope you find this useful. Your server shouldn't be the only thing that caused your bill to spike up. Your toaster oven and coffee maker do more damage compare to your server without a monitor.

Energy Hogs
5000 watts Electric oven
5000 watts Clothes dryer (electric)
3800 watts Water heater (electric)
3500 watts Central Air Conditioner (2.5 tons)
1500 watts Microwave oven
1500 watts Toaster (four-slot)
900 watts Coffee maker
800 watts Range burner
500-1440 watts Window unit air conditioner
200-700 watts Refrigerator
60-100 watts Light bulb 

Fans
100 watts Floor fan or box fan (high speed)
15-95 watts Ceiling fan 

**Computers **
140-330 watts Desktop Computer & 17" CRT monitor
1-20 watts Desktop Computer & Monitor (in sleep mode)
120 watts 17" CRT monitor
40 watts 17" LCD monitor
45 watts Laptop computer

Other
60-100 watts Regular light bulb
4-165 watts Video game (While playing game, 30W for PS2, 70W for XBox, and 165W for XBox 360. See full report at DX Gaming)
55-90 watts 19" television
18 watts Compact fluorescent light bulb
4 watts Clock radio

---

### Post by galeron on 2007-09-13
Or would it be possible for the TS to use a cron job to shutdown the computer automatically at say 2am and wake up at 6pm when he comes back from work?

Would it even be possible to make the computer wake up by itself at a predetermined time? Or am I just wishing?

---

### Post by netlogic on 2007-09-13
Look into "Wakeup On Lan" and you can set a cron job on another machine to send  WOL packets to wake up the machine.

---

