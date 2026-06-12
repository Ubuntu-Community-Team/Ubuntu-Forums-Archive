---
title: "Can you please shine some light on the Circuit mentioned in this email?"
date: 2008-10-21
forum: The Cafe
---

### Post by mickbuntu on 2008-10-21
[SIZE=3]First this is very technical and knowledge is needed in the subject.

Hello, this is directly from my personal email. Why would I let millions read it? Because I need some help, it does not involve my personal life. The person does not wish to help me and all in his rights. If you have no problem helping another human being. Where the buyers  price is respect "in Ubuntu's spirit" (both ways) feel free to help me.  Now on with the email here we go.


> 

Hello,


         I'm writing in a haste, because of wanting to know the answer priorly then write. So forgive my English I'm writing as fast as I can think. 


_**Your Site:**_

Can you please tell me how does this circuit work down to bare?  [http://www.iroquois.free-online.co.uk/index.htm](http://www.iroquois.free-online.co.uk/index.htm)
 
.  I know all the components, I took courses for a while. But I can't understand the logic  behind this circuit (bare-bones).   How does the circuit go to work?   How do you know which IC to use?  It does not seem like a god gift.  

[U][B]
External Site:[/B][/U]

Or, [http://www.aaroncake.net/CIRCUITS/lowvolt.asp](http://www.aaroncake.net/CIRCUITS/lowvolt.asp)
 
. What is behind that circuit?   How does the R2 force the siren to go on (and setting resistance on it forces at a certain voltage drop)?


      How does Aaron cake know to use a specific IC?   And how are the components used here?   Thanks

[html]

Part       Total Qty.          Description             Substitutions
R1, R3       2            1K 1/4W Resistor    
R2           1                5K Pot    
U1           1            LM339 Op Amp IC    
D1           1            1N5233B Zener Diode    
D2           1                    LED    
BZ1          1                Piezo Buzzer    
MISC         1          Board, wire, socket for IC        [/html]

                       /|\

_**Example I know from Aaron cake's circuit above (labeled external site) :**_

    *  Resistors restricts current / voltage flow.
    * The integrated IC made up smaller circuit connects to work.
    * A Diode forces electrical flow one way. It can be forward biased, backward biased.
    * A Led  diode emits the light.
    * The buzzer sound the circuit.
* Board wire etc self explanatory.

          My problem is taking the knowledge of the components (transistors, capacitors etc.... etc......) and making my own circuits. How do you guys / gals make your own circuits? I know all the components to know. Yet I can follow a Schematic, understand it most of the time. But  never actually made a circuit of my own.  Because I do not know how to do it.  Please, can you be kind enough as a Human being tell me?  What do I need to know to design my own circuits?   It is like you give me components. But what do I do with them to make them useful.  I see cool circuits all the time being created. How do we choose IC's  for various circuits?

[/SIZE]

---

### Post by Badly Overdrawn Boy on 2008-10-21
I can't comment on the first circuit, as your link doesn't take me there, just to the home page.

The second circuit works roughly as follows. I don't have time to take a detailed look, but I'll try to answer as best i can.

The zener diode provides a fixed voltage to the positive input of the amplifier. The voltage to the negative input of the amplifier is set using the pot, but drops as the supply voltage drops. If the voltage at the negative input exceeds that at the positive input, nothing happens, as there is no ouput from the amp. At a certain point however, as the supply voltage falls, the voltage to the negative input will fall below the voltage at the positive input. This positive voltage difference will be greatly amplified by the amplifier, and the output (which is basically a transistor) will allow current to flow through the buzzer and LED to ground, and they will then buzz / light up. Once the supply voltage falls even further, the buzzer and light will eventually stop.

I hope this helps!

---

### Post by mickbuntu on 2008-10-21
Very odd I was not notified of any replies. Ususally get sent an Email. Thank you very much for answering part of my question. Do you have any advice though? So I can build my own circuits **_(building blocks mindset). _**What does it take to design them? Aside from understanding what the components do. How does the person say "Hey you know what? I'll build a timer today from scratch, a small amplifier a.. a... a ... a....  you get the idea. 

The second link was: [http://www.iroquois.free-online.co.uk/lithled.htm](http://www.iroquois.free-online.co.uk/lithled.htm) 

> I don't have time to take a detailed look, but I'll try to answer as best i can. 


Thank you again you made an effort and i'm humanly thankful.





> **Badly Overdrawn Boy said:**
> I can't comment on the first circuit, as your link doesn't take me there, just to the home page.

The second circuit works roughly as follows. I don't have time to take a detailed look, but I'll try to answer as best i can.

The zener diode provides a fixed voltage to the positive input of the amplifier. The voltage to the negative input of the amplifier is set using the pot, but drops as the supply voltage drops. If the voltage at the negative input exceeds that at the positive input, nothing happens, as there is no ouput from the amp. At a certain point however, as the supply voltage falls, the voltage to the negative input will fall below the voltage at the positive input. This positive voltage difference will be greatly amplified by the amplifier, and the output (which is basically a transistor) will allow current to flow through the buzzer and LED to ground, and they will then buzz / light up. Once the supply voltage falls even further, the buzzer and light will eventually stop.

I hope this helps!

---

### Post by Tamlynmac on 2008-10-21
There's a circuit design program that is fairly simply to use and extremely well designed with many optional components. By placing your components on the bread board you can actually view the results and change components to modify results. See details here:

[http://ktechlab.org/](http://ktechlab.org/)

I believe this program is available in the Synaptic Package Manager for installation.

---

