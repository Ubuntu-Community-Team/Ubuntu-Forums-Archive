---
title: "Running Steam/Couter S.. Source... Real Laggy..."
date: 2008-12-08
forum: Wine
---

### Post by tgdrums1990 on 2008-12-08
Here is what I have done so far. 

Installed Wine, then the Gecko pagage for it

Copied all windows xp texts in the the texts folder, orginally I just did the tahoma, but it was cashing steam to crash so I added all the .t? files windows had, and stem quit crashing upone start up. 

I can now run Steam, but it is incredibly laggy, and when I try to run Source on it, it bombs out on itself. It kinda runs, I can hear sound but the screen is stuck on the display menue. 

I hear of many running Source here with no issues, I know my pc is capable of this... Cause it ran fine under windows. 

So theres gota be somthing thats cuasing this. 


My pc is running the High fancy display setting... If that helps, but it dnt get any video lag so.... 

TIA... 
Trevor

---

### Post by Brynster on 2008-12-08
ok firstly some specds would be help.

What video card, what ubuntu Version, What Wine Version etc.

But i am guessing your on an ATI based graphics card and i will assume the drivers are installed correctly (this combo causes the most problems hence the guess)

I would set the launch option to "-directx 81 -width 1024 -height768"

do this by right clicking in steam on the source game you want to run then click on properties and add the text between the "" marks (don't include the ""'s though)

and let us know how you get on from there.

---

### Post by tgdrums1990 on 2008-12-08
Oh yes pc specs. 

AMD 3800 X2
1 gig of DDR2 800
ATI Onboard 690V chipset.

---

### Post by tgdrums1990 on 2008-12-08
Ok so made that change. It allowed me to run Source without locking up my pc however it just displayed the main page, and then it ha d a jumpy picture that just showed the main page with no text off center...

---

### Post by luposolo on 2008-12-08
have you tried using the option virtual desktop in winecfg

---

### Post by tgdrums1990 on 2008-12-09
> **luposolo said:**
> have you tried using the option virtual desktop in winecfg

Yes, i am scractching my head at why this is s laggy. It just dosen't add up. I un-installed wine and reinstalled it, basically removing the files and replacing them with new ones. 

Anyways, please help. I wanna play CSS, and dn't wanna go back to windows Today it took me me 2 min to decode, and burn a music cd under windows it took me 10...

---

### Post by karth on 2008-12-10
Just a thought

I have faced lag a while ago in Source games, I happened to change the active tab in Steam before the game actually launched (during loading).
If the game launched while Steam was displaying Store or Community tab, it ran fine. But any of the latter three (which lag a lot themselves) caused the game to stutter...

---

### Post by tgdrums1990 on 2008-12-10
> **karth said:**
> Just a thought

I have faced lag a while ago in Source games, I happened to change the active tab in Steam before the game actually launched (during loading).
If the game launched while Steam was displaying Store or Community tab, it ran fine. But any of the latter three (which lag a lot themselves) caused the game to stutter...

Nope not thats do it... To be honest. What im experiencing is just wine lag over all. It takes my steam client 30secs to log in... IN windows it takes half that iff that... ANd im not sure how to cure this, im very new to linux.

---

