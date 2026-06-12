---
title: "How do soda fountains know when to stop?"
date: 2009-01-15
forum: The Cafe
---

### Post by dfreer on 2009-01-15
Hi everyone,

EDIT: I know this is a silly topic, that's why it's in the Cafe. Just wanted to engage in a discussion and hopefully learn something that had been bugging me. :D

  In a fast food restaurant, they have the soda pop dispensing machines that consist of the nozzle, a lever that extends down, and the tray. When you lean the cup against the lever, it dispenses the drink, and if you leave the cup against the lever, once the drink is full it will stop dispensing. Here's a link to a picture of one if you don't know what I'm talking about (low quality, hard to see the levers):

[http://www.openrussia.ru/imgs/products/logos/3388.jpg](http://www.openrussia.ru/imgs/products/logos/3388.jpg)

   I was just searching online although I didn't get any help, thought I would ask here: How does the machine know when the drink is full? 

Is it measuring the weight of the liquid in the cup pressing against the lever? I don't think it is, since you can manually press against the lever and it will continuously flow without interruption.

Maybe a sensor located in the nozzle pointing down, that detects distances and can tell when the liquid is nearing the top? I think this would be hard to implement, but I wouldn't know.

Is there a sensor/valve located in the bottom of the tray that detects when liquid is in the tray, having overflowed from the cup?

Any thoughts or does anyone know?

---

### Post by RichardLinx on 2009-01-15
On the 'soda' dispensers here they have seperate buttons small, medium, and large. :)

---

### Post by Firestem4 on 2009-01-15
Richard is right. The amount dispensed is usually preset to container certain sizes. So a person just needs to press the right size for their cups. (Generally though...you would want to use their cups or else you might spill if yours is too small)

---

### Post by MaxIBoy on 2009-01-15
Try an experiment:
Poke a hole in the bottom of a cup, then fill it up. See what happens.

---

### Post by ghindo on 2009-01-15
How do they do it?

*Magic.*

---

### Post by EdThaSlayer on 2009-01-15
I guess that the technology that these soda fountains are made out of is far beyond any normal human to comprehend. Aliens helped us build it, getting us fatter so when they do come they can harvest us,our protein, for fuel. *been playing too much Prey*

---

### Post by adamlau on 2009-01-15
I've see the guys across the counter at McDonald's work such magic before...

---

### Post by renzokuken on 2009-01-15
> **EdThaSlayer said:**
> I guess that the technology that these soda fountains are made out of is far beyond any normal human to comprehend. Aliens helped us build it, getting us fatter so when they do come they can harvest us,our protein, for fuel. *been playing too much Prey*

yeah? i heard they reverse engineered it from the space craft that "never" landed at Roswell

---

### Post by bufsabre666 on 2009-01-15
in the one you have pictured it works by using the weight of the liquid and the cup itself as a lever, the weight of the cup keeps it on the bar holding it down until theres so much of the cup filled that it balances it out level thus removing itself from the pour bar

---

### Post by init1 on 2009-01-15
> **dfreer said:**
> 

Maybe a sensor located in the nozzle pointing down, that detects distances and can tell when the liquid is nearing the top? I think this would be hard to implement, but I wouldn't know.

Might not be that hard to do. They are measuring devices that work by bouncing a signal off an object and then calculating how far it is. I'm not sure though if it works quite the same way for liquids.

---

### Post by Johnsie on 2009-01-15
It's not weight... I used to work for mcd's when I was a student and you could fill a cup while holding it in the air. I think it's timer based. The machine knows how much liquid comes out of in a certain time depending on the pressure. There is probably a sensor detecting the pressure of liquids coming through.

> if ($pressure==10)
{

$smallCupSeconds = 3;
$mediumCupSeconds = 6; 
$largeCupSeconds = 8 ;

}

The fact that pressure may be changing while the cup is being filled needs to be accounted for though... I'm not a physicist so I'm not even going to try working that out.

---

### Post by bufsabre666 on 2009-01-15
> **Johnsie said:**
> It's not weight... I used to work for mcd's when I was a student and you could fill a cup while holding it in the air. I think it's timer based. The machine knows how much liquid comes out of in a certain time depending on the pressure. There is probably a sensor detecting the pressure of liquids coming through.

the machines mcdonalds uses is a differnt thing (the mcdonalds ones now have buttons for different sizes) the one pictured in the original post is a model used in arbys/kfc/taco bell and the like, theyre simply a button and a pump requiring weight to hold down the bar (either manual, you holding it, or mechanical, the weight of the liquid coming down holding it) when the level of liquid reaches the spot where the liquid is impacting it will level itself out thus removing weight from the lever and stopping the pump.

we (the nerd of the school) did a whole an event in 8th grade (the science olympiad) and one of them involved these machines. plus this is easily verifiable, goto a location with one of these machines, order a couple different sized drinks and try it out

---

### Post by dfreer on 2009-01-15
> **ghindo said:**
> How do they do it?

*Magic.*

> **EdThaSlayer said:**
> I guess that the technology that these soda fountains are made out of is far beyond any normal human... blah blah blah something about aliens blah blah

Thanks for the lolz guys! :D

> **RichardLinx said:**
> On the 'soda' dispensers here they have seperate buttons small, medium, and large. :)

> **Firestem4 said:**
> Richard is right. The amount dispensed is usually preset to container certain sizes. So a person just needs to press the right size for their cups.

> **bufsabre666 said:**
> the machines mcdonalds uses is a differnt thing (the mcdonalds ones now have buttons for different sizes)

On the machine at my work (independent wings/ribs restaurant) there is absolutely no buttons, and the machine works as described with various sized cups, although I've really only seen a styrofoam 16-20 oz cup be used (mine) and a plastic slightly thinner 16-20 oz cup (used for customers).

Thanks for the replies though, regarding this method of liquid refreshment dispensement!

> **bufsabre666 said:**
> in the one you have pictured it works by using the weight of the liquid and the cup itself as a lever, the weight of the cup keeps it on the bar holding it down until theres so much of the cup filled that it balances it out level thus removing itself from the pour bar

This sounds about right; I will check at work tonight and see if this is the case. If I understand it correctly, the cup is inclined backwards pressing against the lever, with the weight of the incoming liquid keeping pressure against the lever. When the cup is full, the cup levels out and removes pressure from the lever stopping the liquid?

I'll have to test with different cup sizes/shapes at work tonight, I'll let you guys know the results!

---

### Post by dfreer on 2009-01-15
So at work tonight, found out the dispenser works with just about any size cup that will fit under the nozzle (didn't try anything really small like 2-4 oz though). 

Asked around, one person suggested that the liquid overflowing from the cup, then touching the metal level produced an electrical short causing the machine to stop pouring.

Another (a night manager) claimed that there is a "splash" sensor located near the nozzle, when the liquid is near the top of the cup (e.g. the bottom of the nozzle) it splashes up on the sensor. He also claimed that the sensor getting sticky/dirty is the cause of various spurts/malfunctions.

I tried to check during my shift whether the bufsabre666 was correct: If I understand it correctly the cup should be leaning back on the lever to start, and then when full the liquid should lean it forward to disengage the lever. I was unable to verify that this is the case, didn't appear like any "shifting" of the cup occurred.

---

### Post by amitabhishek on 2009-01-16
When you shoot so much of load then you better know when to stop!

---

