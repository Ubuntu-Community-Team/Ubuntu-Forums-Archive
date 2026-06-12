---
title: "building a remote physical computer on off switch"
date: 2012-02-03
forum: The Cafe
---

### Post by Media BCD on 2012-02-03
Alright here's the explanation.

I run a recording studio and unfortunately the new computers are waaaay too noisy, so I need to move them to a machine room. On my desk (where my mix controller is set) i have space to embed a few switch that could be used to turn on and off equipment that I will place in the machine room to reduce the noise of the control room.

My question is here is how can I built a physical on off switch that would run from my machine room to my desk so I can turn on and off the computers?

Thanks for the help guys.

---

### Post by Lars Noodén on 2012-02-03
There are several devices on the market that can turn on and off wall current.  Here is one:

[http://kd85.com/ip-power-9258.html](http://kd85.com/ip-power-9258.html)

Or you could build one, if you have the shop for it.  I built one that is considerably more complex:

[http://www.bsdly.net/~lars/Distance-Ed-server/des.html](http://www.bsdly.net/~lars/Distance-Ed-server/des.html)

---

### Post by Grenage on 2012-02-03
> **Media BCD said:**
> My question is here is how can I built a physical on off switch that would run from my machine room to my desk so I can turn on and off the computers?

The solution could be as simple as a push-button with a wire run to the PC, or as elaborate as Lars' suggestions.  I'm not sure if those options actually turn on the PC, but I've seen some BIOS' which will turn of the PC after power is restored after a fail.

---

### Post by Media BCD on 2012-02-03
> **Grenage said:**
> The solution could be as simple as a push-button with a wire run to the PC, or as elaborate as Lars' suggestions.  I'm not sure if those options actually turn on the PC, but I've seen some BIOS' which will turn of the PC after power is restored after a fail.


My machine room is about 30 feet away, is there a limit to wiring that I should worry about?

---

### Post by Lars Noodén on 2012-02-03
> **Media BCD said:**
> My machine room is about 30 feet away, is there a limit to wiring that I should worry about?

Not really.  If it were not for fire / safety code to worry about you could just run an extension cord to the other room and plug that into the switch on your desk.

---

### Post by juancarlospaco on 2012-02-03
[B]ssh root@ip
sudo shutdown now[/B]

---

### Post by mips on 2012-02-03
You could always use a relays to activate the power switch on the front of the pc. You can control all the relays via something like ardinio i suppose.

---

### Post by Paqman on 2012-02-03
> **mips said:**
> You can control all the relays via something like ardinio i suppose.

Or just a simple switch.

---

### Post by alexfish on 2012-02-04
three switches + wire per computer

One switch ON/OFF for mains

connect two pair of wires to the motherboard jumpers, power on and reset , connect each pair to Push to make switch ..

---

### Post by eriktheblu on 2012-02-04
I wouldn't recommend a hard power cut, as this can result in issues with the software (not sure about modern equipment, but in years past it could also damage HDDs)

Simple way to do it safely (assuming these are linux machines), would be to send hibernate and wake commands over the network (assuming you have a connected device by your desk). You would want to create scripts. This will of course be a slightly involved setup, and may require you to modify BIOS settings. Still easier than the hardware option.

Hardware option: Assuming the power button on the offending computers is connected to a hibernate function, you could wire relays to that. Disadvantage here is that generally the same button is used to hibernate and wake the machine. I would use a relay for each machine wired in parallel with the power switch. Not sure if they make adapters for this, or if you will actually have to splice. If the MOBOs have multiple power button connectors, all the better. 30' probably isn't going to be a big deal, so I wouldn't bother with hardwiring AC components. 

If you wire all the machines together to a single button, it will hibernate those that are on and wake or power on the others. You could alternatively wire each computer with a different switch, and an indicator for each connected to a power indicator on the same machine. This way you see a light, you press the button to turn off.

---

### Post by mips on 2012-02-04
> **eriktheblu said:**
> 
Simple way to do it safely (assuming these are linux machines), would be to send hibernate and wake commands over the network (assuming you have a connected device by your desk). You would want to create scripts. This will of course be a slightly involved setup, and may require you to modify BIOS settings. Still easier than the hardware option.

Dunno why this skipped my mind. This is probably the best option out there, I think you even get remote GUIs if you are not into scripts.

---

### Post by detroit/zero on 2012-02-05
> **Media BCD said:**
> Alright here's the explanation.

I run a recording studio and unfortunately the new computers are waaaay too noisy, so I need to move them to a machine room. On my desk (where my mix controller is set) i have space to embed a few switch that could be used to turn on and off equipment that I will place in the machine room to reduce the noise of the control room.

My question is here is how can I built a physical on off switch that would run from my machine room to my desk so I can turn on and off the computers?

Thanks for the help guys.
As a skilled electronic technician, with nearly ten years in the business of repairing electronic circuitry, and as a former electrician with experience doing residential, commercial, and industrial wiring, I can say the following things with confidence:


[LIST]
[*]You will not find a ready-made application that is out-of-the-box ready. You will have to make this yourself, or find someone with the knowledge to do it;
[*]What kind of switches you use depend entirely on what kind of switches are already installed in your computer, how old the computer is, how you want to power them down, etc.;
[*]You do not want to use relays to switch your mains voltages on or off until the machine has been properly shut down;
[*]You do not necessarily want to go soldering things onto your motherboard as others have suggested. Thirty feet of wires (likely more if you plan on running the wires through walls or air ducts or whatever to keep them out of sight) will cause significant inductive kickback voltage to develop every time the switch is used - the switches (really, your motherboard and power supply) will need to be protected with diodes and capacitors in-line. You will probably also want some kind of digital circuit in place to further isolate (and protect) your valuable equipment;
[/LIST]
I've attached a quick sample circuit I drew up to give you an idea of what will be required. In it, I recommend using your PCs 5V supply, but in reality that may not be entirely practical.

In truth, as someone else mentioned, using SSH or RDP to hibernate your PCs would be a far more realistic approach.

---

### Post by linoseros on 2012-02-05
I think that there's an option on the BIOS that you can set to power on automatically the pc

---

### Post by mips on 2012-02-05
> **linoseros said:**
> I think that there's an option on the BIOS that you can set to power on automatically the pc

[Wake-on-LAN]("http://en.wikipedia.org/wiki/Wake-on-LAN")

---

### Post by robsoles on 2012-02-07
Like detroit/zero I have some experience in the electronics industry and I will add tuppence here.


Thirty feet is a lot of wire and the required current might not traverse the distance very well at all if somebody just puts a dual pin 0.1" header connector on one end of some figure eight and MOM(n/o) switch at the other end - the current being used to sense the button press at the motherboard would have to travel 60 feet and you'd want a really really good conductor to [COLOR=Blue]do[/COLOR] that.

detroit/zero's circuit looks to me like he would introduce an external 5V supply and tie the grounds, not an evil or wicked thing to do but it still relies on the expectation of the current behind the 5V being sufficient to travel the thirty feet - with the extra juice from an external 5V supply it would probably work just fine but (without actually doing any math or properly considering situation and requirements for doing it that way) I think it isn't horribly efficient.

Also, if I am not mistaken one resistor, the wire, a MOM(n/o) switch, an [opto-coupler]("http://en.wikipedia.org/wiki/Opto-isolator") [COLOR=Blue](per PC)[/COLOR] [COLOR=Blue]and[/COLOR] DC source [s]and one resistor[/s] to power-on remotely should suffice to do it professionally enough.

*** I would loathe using this button to shut them down because my options are "press momentarily now and then go and check the system in question physically anyway" or "press and hold for 4.9+ seconds and cross my fingers it wasn't writing anything too crucial in disk space at the magic moment"


I think that if I set about this endeavour I would briefly investigate going wireless and end up settling on an [opto-coupler]("http://en.wikipedia.org/wiki/Opto-isolator") **per** PC I wish to control remotely and then hacking out a 12V or 24V rail in the studio equipment, then I would find the resistance in my run of wire, subtract that from the required [current limiting resistor]("http://en.wikipedia.org/wiki/LED_circuit") and feed my 12V or 24V to the opto-coupler via a MOM(n/o) switch and the resistor;

Expectations: External DC source can't reach the MOBO, opto-coupler (must be wired with correct polarity both on MOBO side and on DC source side) looks just like the switch to the circuitry in the MOBO. The 12V or 24V rail was always going to be there and I am definitely not loading it while the button isn't depressed and it is not a significant load when it is being pressed anyway.

If you really really badly want a schematic I shouldn't procrastinate too long before I go from my napkin here to Protel (or something) for you :)

---

### Post by spynappels on 2012-02-07
If you use an iPhone/iPad or Android phone/tablet, there are apps available for SSH to shut the computers down and Wake-on-LAN apps to switch them on again. The SSH shutdown could probably be recorded as a Macro or shortcut, and Fing (on Android at least) allows you to send WoL packets to any node on your network.

At least you shouldn't need to add any infrastructure stuff, assuming you already have a wireless network.

---

### Post by robsoles on 2012-02-07
@spynappels: If it is wireless then I gotta say I am yet to see one that can connect while its computer is off but I suppose it is in the realms of possibility.

Yep, must use SSH (or RDP if these are Windows machines) to shut them down nice for sure - I still wouldn't leave the same premises they are in without physically checking them before going anyway :p

I would bypass 'wake on lan' assuming that one or more of the following factors was going to be more hassle than it is worth: Any NIC amongst PCs I wish to power on remotely may not even have power when the PC is off (not many modern PCs but who is running a full book of all modern PCs?), I would assume I wasn't going to get it done over a wireless network unless I just did a wireless variant of my prior suggestion so I need to route if I have more than two machines and the router may actually actively block something about any of the required packets and stopping it from doing so may be more hackish than pretty menu items all the manufacturers seem to use these days.

I've had each of these situations turn up as a blocker when asked to organise a wake on LAN setup for anybody (about half were problematic like this, half no real blockers but still...), all of them found work-arounds like "BIOS->Wake->On power restored" or something and nobody pressed me for a method beyond such.



Now, back to my foolishly volunteering a method that came to mind earlier...

Sorry, OK, reconsideration: It is a recording studio and ground loops aren't a good thing when you are trying to do high fidelity audio stuff. This should occur to me should I start (even contemplating a schematic, let alone) trying to do it for real in an actual recording studio.

If you are having a recording studio and you don't know the slightest thing about ground loops and why you want to minimise them in your set up then you should find out IMO.


The DC source should be an ungrounded plug-pack, due using current limiting and calculating the drop in the cable it should be possible with a 5V plug pack but I (feel a bit driven to) recommend a 12V plug pack if you do it this way. I should check a book from a shelf near me but, pending the grade of the wire, I *think* the wire alone may be a much more significant load to a 5V source than a 12V one - maybe the effects I am thinking of are more relevant in AC than DC.

(OK, just did quick couple of Googles and over 30 feet 12-24V is favorable enough over 5V - optocouplers come in wide operating voltage ranges and (assuming efficient transformer etc) the higher the voltage the more efficiently it is delivered and used. However, higher voltages are more dangerous and it is probably really best at 12V :roll:)

I really should easily be able supply a schematic and simple enough instructions if anyone is the least bit interested, it wouldn't surprise me too much if I can find someone else's "prior art" using Google that I could link to instead of actually having to fire up virtualbox (to whip it up in protel) and draw it myself :p

---

### Post by spynappels on 2012-02-07
> **robsoles said:**
> @spynappels: If it is wireless then I gotta say I am yet to see one that can connect while its computer is off but I suppose it is in the realms of possibility.


I was actually assuming there would be a wired element to the network as most wireless routers now have ethernet ports too. I also assumed that kit in a recording studio would be mid to high end, so WoL would be available on the NICs. This should avoid any ground loop problems etc as no new (electrical/electronic) kit would be added.

---

### Post by robsoles on 2012-02-07
> **spynappels said:**
> I was actually assuming there would be a wired element to the network as most wireless routers now have ethernet ports too. I also assumed that kit in a recording studio would be mid to high end, so WoL would be available on the NICs. This should avoid any ground loop problems etc as no new (electrical/electronic) kit would be added.Good point, well worth checking if WoL is viable right round indeed - betcha didn't think I would admit it so quick, huh? :p

---

### Post by spynappels on 2012-02-07
> **robsoles said:**
> Good point, well worth checking if WoL is viable right round indeed - betcha didn't think I would admit it so quick, huh? :p

:lolflag:

---

