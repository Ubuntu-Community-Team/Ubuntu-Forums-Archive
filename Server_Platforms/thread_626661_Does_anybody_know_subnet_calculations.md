---
title: "Does anybody know subnet calculations?"
date: 2007-11-29
forum: Server Platforms
---

### Post by jingo811 on 2007-11-29
I searched for this in google: 3com "ip addressing" pdf
and downloaded that file.  But the font becomes weird when reading it on Ubuntu.  So I clicked on the html version in google.
[http://216.239.59.104/search?q=cache:CdTkfeKi7kAJ:www.3com.com/other/pdfs/infra/corpinfo/en_US/501302.pdf+3com+%22ip+addressing%22+pdf&hl=en&ct=clnk&cd=1&client=firefox-a](http://216.239.59.104/search?q=cache:CdTkfeKi7kAJ:www.3com.com/other/pdfs/infra/corpinfo/en_US/501302.pdf+3com+%22ip+addressing%22+pdf&hl=en&ct=clnk&cd=1&client=firefox-a)

I have problem at Page 19 which says page 17 at the bottom.
**My question:**  
If I don't have the luxury of time to do a 511 rows chart at an exam.  And needs to pin-point the ip-address/subnet format for lets say Subnet #9.
What kind of mathematical formula can I use in order to put in the value 9 and then calculate the entire Extended Network Prefix for /25?
Using only pen and paper.

```

Base Net: 10001100.00011001 .00000000.00000000 = 140.25.0.0/16
Subnet #0: 10001100.00011001.**00000000.0** 0000000 = 140.25.0.0/25
Subnet #1: 10001100.00011001.**00000000.1** 0000000 = 140.25.0.128/25
Subnet #2: 10001100.00011001.**00000001.0** 0000000 = 140.25.1.0/25
Subnet #3: 10001100.00011001.**00000001.1** 0000000 = 140.25.1.128/25
Subnet #4: 10001100.00011001.**00000010.0** 0000000 = 140.25.2.0/25
Subnet #5: 10001100.00011001.**00000010.1** 0000000 = 140.25.2.128/25
Subnet #6: 10001100.00011001.**00000011.0** 0000000 = 140.25.3.0/25
Subnet #7: 10001100.00011001.**00000011.1** 0000000 = 140.25.3.128/25
Subnet #8: 10001100.00011001.**00000100.0** 0000000 = 140.25.4.0/25
Subnet #9: 10001100.00011001.**00000100.1** 0000000 = 140.25.4.128/25
.
.
Subnet #510: 10001100.00011001.**11111111.0** 0000000 = 140.25.255.0/25
Subnet #511: 10001100.00011001.**11111111.1** 0000000 = 140.25.255.128/25
```






**This is the only clue I got from a simpler example.  But I can't adjust that formula to the more complicated subnet format in the above problem**
At page 15 which says 13 at the bottom.

[COLOR="DarkRed"]An easy way to verify that the subnets are correct is to ensure that they
are all multiples of the Subnet #1 address. In this example, all subnets
are multiples of 32: 0, 32, 64, 96, and so on.[/COLOR]



The eight subnet numbers for this example are listed in the following
code sample. The underlined portion of each address identifies the
extended network prefix, while the bold digits identify the 3 bits repre-
senting the subnet number field:

```
Base Net: 11000001.00000001.00000001 .00000000 = 193.1.1.0/24
Subnet #0: 11000001.00000001.00000001.**000** 00000 = 193.1.1.0/27
Subnet #1: 11000001.00000001.00000001.**001** 00000 = 193.1.1.32/27
Subnet #2: 11000001.00000001.00000001.**010** 00000 = 193.1.1.64/27
Subnet #3: 11000001.00000001.00000001.**011** 00000 = 193.1.1.96/27
Subnet #4: 11000001.00000001.00000001.**100** 00000 = 193.1.1.128/27
Subnet #5: 11000001.00000001.00000001.**101** 00000 = 193.1.1.160/27
Subnet #6: 11000001.00000001.00000001.**110** 00000 = 193.1.1.192/27
Subnet #7: 11000001.00000001.00000001.**111** 00000 = 193.1.1.224/27
```

---

### Post by jingo811 on 2007-11-29
I think I found a possible formula to calculate desired:
Subnet #number => ip-address/subnet mask format

```
X = Subnet #7

( X *128) / 256 = 3.5

=> x.x.3.128/25

```

Can somebody confirm if this is correctly thinked?

---

### Post by crouton on 2007-11-29
Try [http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php)

Easier than doing it by hand, but I have to commend you for the effort. :)

[edit] Not exactly sure that it will solve your specific problem but it should help you verify your results (I think.)

---

### Post by MJN on 2007-11-29
The problem with defining such an abstract 'quick shot' formula is that you're moving further and further away from the mechanics of subnetting and so run the risk of misunderstanding what's actually going on.
 
Try the following methodology instead (using the same scenario as that example for comparison):
 
1. We've got a /16 address range to play with (140.25.0.0/16) hence we've got 16 bits fixed and 16 bits for use as we wish.
 
2. We are asked to support 60 hosts per subnet and so the least number of bits required to do this is 6 given 2^6 = 64. However, we need to knock 2 off that 64 for the network (all 0's) and broadcast (all 1's) leaving us with 62 hosts max per subnet. As the example discusses this is not good from a future-proofing perspective and so let's go up one bit (to 7) giving us 2^7 = 128. Again, knock 2 off and we are left able to support 126 hosts per subnet.
 
3. So, out of the 16 bits on the right-hand side we are now using 7 of them for the host (h) which leaves us with 9 bits for the network (n):
 
```
General Format: 10001100.00011001.nnnnnnnn.nhhhhhhh
```
 
(The dots must be positioned on the octet (8-bit) boundaries)
 
4. We now have a total of 25 bits for the network portion hence our subnet mask is /25. The 9 bits for the sub-network (n's) gives us 2^9 = 512 subnets. 
 
5. To calculate Subnet #0-511 ignore for now the dot which splits the nnnnnnnn.n sequence and just calculate the binary equivalent of the subnet number. For example, to calculate Subnet #7 convert 7 into binary (=111 without leading zeros) and slot that right-justified (adding zeros to the left to make it 9 bits long) into the nnnnnnnn.n sequence i.e. 00000011.1 which when combined with zeros for the hosts gives us:
 
```
General Format: 10001100.00011001.nnnnnnnn.nhhhhhhh
Subnet #7:      10001100.00011001.00000011.10000000
```
 
6. Converting that back into decimal gives us 140.25.3.128/25 for Subnet #7.
 
7. Let's try Subnet #317 - Convert it into binary (=100111101 without leading zeros) and slot it right-justified (it's already 9 bits long so no zeros to add) into our subnet portion (the n's) and set the h's to zeros:
 
```
General Format: 10001100.00011001.nnnnnnnn.nhhhhhhh
Subnet #317:    10001100.00011001.10011110.10000000 = 140.25.158.128/25
```
 
How does that sound?
 
Mathew

---

### Post by ruibernardo on 2007-11-29
An alternative to a calculator on a webpage as crouton pointed is to use [gip]("http://www.ubuntugeek.com/gip-ip-calculator-for-gnome-desktop-environment.html") from the repositories.

---

### Post by jingo811 on 2007-11-29
> **MJN said:**
>  
 
5. To calculate Subnet #0-511 ignore for now the dot which splits the nnnnnnnn.n sequence and just calculate the binary equivalent of the subnet number. For example, to calculate Subnet #7 convert 7 into binary (=111 without leading zeros) and slot that right-justified (adding zeros to the left to make it 9 bits long) into the nnnnnnnn.n sequence i.e. 00000011.1 which when combined with zeros for the hosts gives us:
 
```
Subnet #7: 10001100.00011001.00000011.10000000
```
 
6. Converting that back into decimal gives us 140.25.3.128/25 for Subnet #7.
 
8. Let's try Subnet #317 - Convert it into binary (=100111101 without leading zeros) and slot it right-justified (it's already 9 bits long so no zeros to add) into our subnet portion (the n's) and set the h's to zeros:
 
```
10001100.00011001.nnnnnnnn.nhhhhhhh
10001100.00011001.10011110.10000000 = 140.25.158.128/25
```
 
How does that sound?
 
Mathew

It's a miracle I can see clearly now :shock: tnx for the examples.  I should have asked you first 2 weeks ago.  Trying to interpret the misguiding explanations and number conventions by reading the Cisco modules and 3COM pdf has given me several days of headaches.

They should have hired you to make those subnetting guides.

---

### Post by MJN on 2007-11-29
:lolflag:

Give it a week and you'll be scratching your head again!

That's the problem with subnetting - there are many ways of approaching what is a somewhat complex issue, particularly as it is quite an alien concept unless you first learnt to count in binary at a young age!

Speaking of binary, I suggest you avoid the temptation to dip out of binary into decimal too early - subnetting relies wholly on the binary representation of numbers and as soon as you convert them to decimal you often lose the visibility of where all the boundaries lie. This is particularly true when a subnet crosses one of the 8-bit boundary points like the example you raised - in decimal it makes no sense, in binary... well at least you've got a better chance!

Feel free to come back with any further queries or to run through a different example (I can make one up if required).

Stick with it - subnetting knowledge is a useful skill to have and can often set you apart from the next guy.

Mathew

---

### Post by jingo811 on 2007-11-29
Tnx you'll probably see more of me when we start learning VLSM in 2nd semester  in our Basic Cisco class.
Until then I have some questions.

**1.) - [ Solved ]**
Why does ppl who writes about subnetting and Wikipedia refer each individual parts of the ip-address as 1 octet?
Why don't they call it 1 byte since it's a more well-known word for 8 bits?

0000 1111  .  0000 1111  .  0000 1111  .  0000 1111 
I like doing spacing for each octet since it reduces mis-reading and human errors even if it's incorrect to do so.  At least I think it's an upgrade from writing everything without typographical aid.  :)




**2.) - [ Solved ]**
In an old TI-85 Assembly tutorial explaining about binary and hex they mentioned

3 bits = 1 octal
4 bits = 1 nibble = 1 Hex
8 bits = 1 byte

Do these belong in the subnetting world or is it just something for the programming world?
Sadly I never got past Chapter 2 so I never learnt to program in TI-Assembly.




**3.) - [ Solved ]**
If I'm an ISP and gives you this ip-address with the subnet mask which belonged to some old company where some admin already subnetted things.
Is it possible to back-engineer the numbers in order to....  

140.25.1.132  /25

.....Calculate and pin-point these 5 things without any further information?
[LIST]
[*]Base Net
[*]Subnet #number
[*]Host #number
[*]Total amounts of subnets
[*]Total amounts of hosts
[/LIST]

If not possible then how would you proceed to get the information you need if you're sitting next to the Networking hardware or something like this?




**4.) - [ Solved ]**
This problem was given by our teacher the second day we learnt about subnetting and he's always quick with his explanations.  Until this day I don't know how to see the answer.
You have 2 ip-addresses and want to find out if you'll need a Router between them or if they can communicate without help.
What do I need to know first before doing the math?  
That lesson went so fast that I might be missing some vital information in my notepad.  Will knowing the Base Net solve this problem?

Do they need a Router to communicate?
171.11.4.18 /29  <==> 172.16.5.67 /29

---

### Post by koenn on 2007-11-29
> Why does ppl who writes about subnetting and Wikipedia refer each individual parts of the ip-address as 1 octet?
Why don't they call it 1 byte since it's a more well-known word for 8 bits?because octet always means 8 bits. byte originally was used for a given, fixed number of bits that a system used, eg for the size of a character, or the length of a memory address. On some systems, a byte was 7 bits, on others, 12, and so on.  

I suppose that, since tcp/ip was meant to be  platform-independent, they preferred to use 'octet'

---

### Post by vallis on 2007-11-29
Hey,
I know you've already got a solution that works for you but I thought I'd let you know the way I like to do it anyway.

for your example I'd do the following:

given 140.25.1.132/25

convert the IP into binary, giving you
10001100000110010000000110000100

the /25 tells you the subnet mask will be
11111111111111111111111110000000
(25 1ns and fill the rest with 0s)
can be converted back to 255.255.255.128 if you need the decimal notation

the total number of subnets is 2 to the power 25 (the number of 1ns)
giving you 33,554,432
the total number of hosts per subnet is 2 to the power 7 (the number of 0s)
giving you 128 hosts per subnet

took me ages to get my head round that.
have fun and good luck in your exam.

[edit] almost forgot, you need to take 2 away from the number of hosts and subnets to allow for broadcast and network name. so it ends up being  33,554,430 and 126. [/edit]

---

### Post by koenn on 2007-11-29
> 2.)
In an old TI-85 Assembly tutorial explaining about binary and hex they mentioned

3 bits = 1 octal
4 bits = 1 nibble = 1 Hex
8 bits = 1 byte

Do these belong in the subnetting world or is it just something for the programming world?
Sadly I never got past Chapter 2 so I never learnt to program in TI-Assembly.
It's more general computer stuff.
eg with 3 bits you can represent 8 numbers ( 000 to 111 binary), so 8 -> octal
4 bits -> 16 numbers -> Hexa-decimal
Octal and especially Hex are used because they're convenient to represent binary nmbers in a shorter form, eg 2 hexadecimal numbers = 2x 4bits = 1octet (or 1 byte, because nowadays, bytes are mostly 8bit)

---

### Post by jingo811 on 2007-11-29
**3.)**
If I'm an ISP and gives you this ip-address with the subnet mask which belonged to some old company where some admin already subnetted things.
Is it possible to back-engineer the numbers in order to....  

140.25.1.132  /25

.....Calculate and pin-point these 5 things without any further information?
[LIST]
[*]Base Net
[*]Subnet #number
[*]Host #number
[*]Total amounts of subnets
[*]Total amounts of hosts
[/LIST]

If not possible then how would you proceed to get the information you need if you're sitting next to the Networking hardware or something like this?


> **vallis said:**
> Hey,
I know you've already got a solution that works for you but I thought I'd let you know the way I like to do it anyway.

for your example I'd do the following:

given 140.25.1.132/25

convert the IP into binary, giving you
10001100000110010000000110000100

the /25 tells you the subnet mask will be
11111111111111111111111110000000
(25 1ns and fill the rest with 0s)
can be converted back to 255.255.255.128 if you need the decimal notation

the total number of subnets is 2 to the power 25 (the number of 1ns)
giving you 33,554,432
the total number of hosts per subnet is 2 to the power 7 (the number of 0s)
giving you 128 hosts per subnet

took me ages to get my head round that.
have fun and good luck in your exam.

[edit] almost forgot, you need to take 2 away from the number of hosts and subnets to allow for broadcast and network name. so it ends up being  33,554,430 and 126. [/edit]

Tnx vallis things are starting to look familiar now.  But regarding Question 3, I guess there's no math to find out about the Base Net?  You'll need to physically access the Network devices and do some commands in the Switches, Routers, or Hubs and find out the Base Net then you could back-engineer some previous Admins subnetting work?

---

### Post by jingo811 on 2007-11-29
> **4.)**
This problem was given by our teacher the second day we learnt about subnetting and he's always quick with his explanations.  Until this day I don't know how to see the answer.
You have 2 ip-addresses and want to find out if you'll need a Router between them or if they can communicate without help.
What do I need to know first before doing the math?  
That lesson went so fast that I might be missing some vital information in my notepad.  Will knowing the Base Net solve this problem?

Do they need a Router to communicate?
171.11.4.18 /29  <==> 172.16.5.67 /29

I think I know now what my old hasty notes are trying to tell me.
Find and take the subnet mask ( Extended Network Prefix ) 
Then find the Base Net ( Network Prefix ) and do this

```
(Extended Network Prefix) - (Network Prefix) = Amount of Subnet number bit.
```

Then I take those 2 ip-addresses and see if they have the same Subnet Number Bits if they do then I won't need a Router between them.  Right? :)

---

### Post by koenn on 2007-11-29
wrong, i think, unless I misunderstand your terminology.
you need a router when hosts are on separate networks, so you'd have to compare the **network** portion of he ip addresses. If they're identical -> same network -> no router.

You can use vallis' method of writing all addresses and masks in binary, check what part of the adresses indicates network, and compare them. 

In this case, I'd guess that with 29 bits network portion in a 32 bit address, you have 3 bits left, enough for 8 host addresses (actually 6 + network addr + broadcast addr) per subnet. As the given ip addresses look more than 8 addresses apart, I'd guess they're on separate networks, and you need a router. 

I could be wrong, of course.

---

### Post by MJN on 2007-11-29
[Edit: Koenn is spot on but here're the workings!]

Are you sure you scribbled the question down right? ;) Or perhaps there is another piece of info missing? The question is valid, but the numbers used are not quite what I'd expect (given it's quite clear from first glance).

Anyway, to solve, you start with the premise that a router is needed between two IP addresses if they are in different subnets. That is, ignoring their host number if their network portions are different then they need routing - if they are the same then they don't.

So, starting with the first IP address we need to find its network: 

```
171.11.4.18/29 written in binary is:

10101011.00001011.00000100.00010010

Given we have a /29 prefix:

nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnhhh

we can find the network by changing the host number to all zeros:

10101011.00001011.00000100.00010000

Hence the network address is 171.11.4.16
```For the second address:

```
172.16.5.67/29 written in binary is:

10101100.00010000.00000101.01000011

Given we have a /29 prefix:

nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnhhh

we can find the network by changing the host number to all zeros:

10101100.00010000.00000101.01000000

Hence the network address is 172.16.5.64
```The network addresses are different hence the IP addresses are in different subnets so you would need a router between them.

Perhaps he was illustrating that even though two addresses might have the **same length** subnet mask this doesn't necessarily mean they are on the same network.

---

Not wishing to sound like your teacher, try these:

5) Host A and Host B have addresses 171.11.15.69/27 and 171.11.15.82/27 respectively. Do they need a router between them?

6) Host A and Host B have addresses 171.11.15.71/27 and 171.11.15.98/27 respectively. Do they need a router between them?

Go on - you know you want to! ;)

Mathew

---

### Post by jingo811 on 2007-11-30
> 171.11.15.69/27 and 171.11.15.82/27

**5.)  No router.**

69 ....................... **010**0 0101
............................ **nnn**h hhhh
............................ **64**

Subnet# A  :  171.11.15.64  /27


82 ....................... **010**1 0010
............................ **nnn**h hhhh
............................ **64**

Subnet# B  :  171.11.15.64  /27

================================================================================

> 171.11.15.71/27 and 171.11.15.98/27


**6.) Yes, needs a router.**

71 ....................... **010**0 0111
............................ **nnn**h hhhh
............................ **64**

Subnet# A  :  171.11.15.64  /27


98 ....................... **011**0 0010
............................ **nnn**h hhhh
............................ **96**

Subnet# B  :  171.11.15.96  /27

================================================================================


```

/8  Class A   0-127
/16 Class B   128-191
/24 Class C   192-223

```

Going by this knowledge I do the above process one more time on the Subnets# in order to find out the Base Net# for each of the 4 given Host# Addresses.  Is this correct thinking?

**5.)**
Base Net# A  171.11.0.0  /16
Base Net# B  171.11.0.0  /16

**6.)**
Base Net# A  171.11.0.0  /16
Base Net# B  171.11.0.0  /16

---

### Post by MJN on 2007-11-30
> **jingo811 said:**
> **5.)  No router.**
[B]
6.) Yes, needs a router.[/B]

Spot on!! I think you've got the hang of this now. (Notice how without converting to binary you stood no (well, little) chance of spotting whether they were in the same/different subnets?)

> ```

/8  Class A   0-127
/16 Class B   128-191
/24 Class C   192-223

```Stop!

We are talking variable length subnet masking here hence classful addressing goes out of the window. As soon as we introduce variable length subnet masks the idea of class A, B etc disappears.

The concept of moving the network-host bit boundary, known as Classless Inter-Domain Routing (CIDR), introduces the /x notation hence if we're talking slash notation we are not talking classful addressing.

For example, the address 25.0.0.0 is no longer a Class A range if we subnet it to 25.0.0.0/x - even when x=8 it's still technically not a 'Class A' range (even though it is the same size as one) given CIDR (with slash notation) is classless. The network 25.0.0.0/24 is only 256 hosts yet a Class A network is 16-million hosts hence since the introduction of CIDR just because it starts 25. doesn't mean it is a Class A.

Confusing, yes, but that's what happens when you change a protocol/concept midway through its life!

Mathew

---

### Post by jingo811 on 2007-12-01
In our course the teacher have only showed some old FLSM examples so far.  We are gonna begin doing some VLSM after Christmas weekends.
So what method do you use in order to go from the given ip-addresses and the calculated Subnets# to finding out the Base Net# for each of the 4 examples?


> 
171.11.15.69/27 and 171.11.15.82/27

Subnet# A : 171.11.15.64 /27
Subnet# B : 171.11.15.64 /27

**5.)**
Base Net# A 171.11.0.0 /16    :confused:
Base Net# B 171.11.0.0 /16    :confused:

================================================


> 
171.11.15.71/27 and 171.11.15.98/27

Subnet# A : 171.11.15.64 /27
Subnet# B : 171.11.15.96 /27

**6.)**
Base Net# A 171.11.0.0 /16   :confused:
Base Net# B 171.11.0.0 /16   :confused:

---

### Post by MJN on 2007-12-01
That's just it - you can't determine the base net from the subnet/address if you're using CIDR. So, say we have the address 171.11.15.69/27 all we know is the subnet it came from (171.11.15.64/27 as previously calculated) but we don't know if that is a subnet from a bigger subnet, which in turn could be a subnet from an even bigger one and so on.

Perhaps if an exam question were to ask you what the base net is then you don't really have the opportunity to question the question and so you'd be better off basing it on the classes as you've mentioned. Incidentally, you don't have to remember the class boundaries (A: 0-127,$ B: 128-192 etc) - although you probably will - but instead you can just look at the how the first octet starts - Class A always starts with a 0, B: 10, C: 110, D: 1110, E: 1111.

I would expect that you'd be normally be *given* the base net and then be asked to subnet it to meet the requirements.

Mathew

---

### Post by jingo811 on 2007-12-01
> **MJN said:**
> That's just it - you can't determine the base net from the subnet/address if you're using CIDR. So, say we have the address 171.11.15.69/27 all we know is the subnet it came from (171.11.15.64/27 as previously calculated) but we don't know if that is a subnet from a bigger subnet, which in turn could be a subnet from an even bigger one and so on.


ic I didn't realize that things would get more complicated than what I've learnt so far.


**Question 7.)**

I'm guessing that most of you guys in here work professionally as admins or have equivalent expertise.
Have you ever been in a situation where you're hired because the previous admin was recently retired from the company.  And now you have to manage whatever work he has done.  Thus you will have to know how he reasoned when slicing up the Network with subnetting.

Is there some Linux program or Command one can use to map out the entire subnetting logic for an ip-address given from the ISP to that company?

Or will I have to write down all the ip-addresses between each router and calculate manually by hand in order to understand how the previous admin thought when he subnetted things several years ago?

---

### Post by MJN on 2007-12-01
Don't be too disheartened by the seemingly-increasing complexity of all this - it sounds like you've got a good understanding already and so you just need to give it time. It's the kind of knowledge that will only be reinforced with further exposure to it - and believe me there will be times when you thought you understood it completely but then will find yourself still scratching your head!

Reverse engineering someone else's network can indeed be difficult particularly as one man's 'straightforward strategy' can easily become another man's headache. This is where documentation becomes important but of course that step is always put off until tomorrow until everything is up-and-running and ends up never getting done!

It all depends on the network you're working on and how complex it is so there's really no simple answer to give. You think it sounds bad now, you wait until you've got multiple VLANs on your networks - things suddenly take an exponential leap in complexity and associated head scratching - but cross that bridge when you come to it!

Mathew

---

### Post by jingo811 on 2007-12-01
Just as I feared.  I hope there's some diagnostic tools for solving the complex scenarios that you described.

**Question 8.)**
I have started to do some exercises from the 3COM pdf.  And I'm wondering if I'm still incapable of grasping this subnetting problem or if 3COM has made some error in their solution.
> 
Assume that you have been assigned the 132.45.0.0/16 network block.
You need to establish eight subnets.
1 __________ binary digits are required to define eight subnets.

**My calculations.**
2^x = 8 subnets
2^3 = 8-2 = 6 subnets  ................................ Not enough bits
2^4 = 16-2 = 14 subnets .............................It will require 4 bits to enable 8 subnets.

> **3COM solution.**
1 Three binary digits are required to define the eight subnets.

Am I going crazy or have 3COM made a mistake?

---

### Post by MJN on 2007-12-01
Ahh. This old chestnut...

Well, errm, 3com haven't made a mistake as such (although see below) so I'll let you make the decision! ;)

When calculating the number of bits required to support a certain number of **hosts** we did indeed knock off 2 to account for the all-zero's and all-one's host bits situation. That is, on a network two 'addresses' are used to identify the network (**host** bits all zero) and the broadcast address (**host **bits all ones).

When it comes to calculating the number of bits required to support a certain number of **networks** we don't (necessarily) have this restriction. It is quite acceptable to have the network bits as all zeros, or all ones. The concept of network/broadcast identification is only applicable to the **host bits**.

** However**, and this is the bit where you might think the rules are being made up as we go along, it is considered good practice by many to not actually utilise subnets that have their network bits set to all zeros or all ones given there can be confusion over whether the address 132.45.0.0/16 is referring to the base network or the first (#0) subnet. Hence, and RFC950 even suggests this (end of Section 2.1 '*It is useful to preserve* ...'), you would be equally correct to not consider the all-zero and all-one subnets as usable.

So what do you do in an exam given there are two arguably-correct answers? Well, this is the point when you hope that the examiner really knows his stuff and is aware of this potential ambiguity. I have seen questions clarify the situation with something along the lines of 'You can assume that the all-zero and all-one subnets are valid.'

Mathew

---

### Post by jingo811 on 2007-12-01
> **MJN said:**
> 
When calculating the number of bits required to support a certain number of **hosts** we did indeed knock off 2 to account for the all-zero's and all-one's host bits situation. That is, on a network two 'addresses' are used to identify the network (**host** bits all zero) and the broadcast address (**host **bits all ones).

When it comes to calculating the number of bits required to support a certain number of **networks** we don't (necessarily) have this restriction. It is quite acceptable to have the network bits as all zeros, or all ones. The concept of network/broadcast identification is only applicable to the **host bits**.


Miracle number 2 :shock: I've always sensed something fishy about the automatic knocking off 2 business when calculating the #Subnet and #Host capacity.  I just couldn't form my suspicions into tangible words.

Tnx for the heads up!

---

### Post by koenn on 2007-12-01
> **jingo811 said:**
> 
**Question 7.)**

I'm guessing that most of you guys in here work professionally as admins or have equivalent expertise.
Have you ever been in a situation where you're hired because the previous admin was recently retired from the company.  And now you have to manage whatever work he has done.  Thus you will have to know how he reasoned when slicing up the Network with subnetting.

Is there some Linux program or Command one can use to map out the entire subnetting logic for an ip-address given from the ISP to that company?

Or will I have to write down all the ip-addresses between each router and calculate manually by hand in order to understand how the previous admin thought when he subnetted things several years ago?
I inherited a network some years back and it was quite weird, but an understanding of subnetting and a decent subnet calculator goes a long way. You don't actually have to understand the other guy's reaoning - you just look at what's there and what the consequences are - along the lines of  i have this network here, and that network there, and they appear connected, so lets find out which routers are involved here ... 
luckily for me, they used a simple 24 bit netmask almost everywhere, which makes addresses easy to read, and there were no VLANs, but I came across quite a few weird routing and NAT sollutions that obfuscated things considerably.

---

### Post by jingo811 on 2007-12-11
10% from failure on the Cisco 1 exam. :) Yessss I made it tnx ppl for your guidance.

---

### Post by MJN on 2007-12-11
Nice one - well done!

Mathew

---

### Post by jingo811 on 2007-12-28
Just wanted to have someone clarify one thing for me which seems to confuse me still.
If the assignment is described as such:

**Example A.)**
> You will be allocated one class C network that you must subnet to provide a logical addressing scheme for the network. 

> You have been given the 192.168.1.0/24 address space to use in your network design. .....

At this point does it mean I only have 1 amounts of nets and 255 amounts of hosts?
```
192.168.1.HOSTS => 1 net
NET.NET.NET.0 => 255 hosts
```

Thus only when I start borrowing bits from the 4th octet do I have access to 2 or more nets.  Now I have subnets correct?




**Example B.)**
The confusion is this how would a problem be formulated specifically in order to allow me to use these as separated nets?
```
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24
```

This one uses C class like the above problem.  But here I can play with and alter the 3rd octet which I couldn't do in the above excercise.
I can't differ these 2 methods apart from another when working physically with all the cisco routers and cables.  The teacher says this is a C class network yet I can alter the 3rd octet which should be locked.
Do you see the confusion in my head :confused:

---

### Post by koenn on 2007-12-28
You're just making things complicated.

if the If the assignment says "You have been given the 192.168.1.0/24 address space to use in your network design' then you're simply not allowed to use 192.168.3.0/24 or 192.168.2.0/24 or whatever. 

Of course they're not "locked". But in real life, someone else will already be using the other address ranges, so if you use those too, routers that need to deliver packets to 192.168.2.0 have no way of knowing wheter that's your network or the other one - it's just not going to work (and you get fired).

---

### Post by The Cog on 2007-12-28
a)
You are right. You have one class C to play with, and to get subnets from it you will hve to chop that last octet up. How much you use as subnet-number / host-number depends on how many subnets/hosts you need, of course.

b)
Your confusion is in thinking that the ip address alone can tell you whether an address range has been subnetted. It can't. From far away on the network, you cannot tell. Its like using long telephone numbers. You can't tell from the number alone how much of it is a block of numbers all on one exchange - businesses can buy small or large blocks of numbers from the PTT.

Some routing protocols will specifically advertise subnets to each other, e.g. 192.168.1.0/28, 192.168.16/28..., and others cannot pass the subnet mask. Even when they can advertise specific subnets, it is common practice to summarise them into larger groups where possible, so that for instance these 4:
192.168.0.0/24
192.168.0.1/24
192.168.0.2/24
192.168.0.3/24
all get advertised as 182.168.0.0/22

---

### Post by jingo811 on 2007-12-28
> **koenn said:**
> 
Of course they're not "locked". But in real life, someone else will already be using the other address ranges, so if you use those too, routers that need to deliver packets to 192.168.2.0 have no way of knowing wheter that's your network or the other one - it's just not going to work (and you get fired).

I still have a hundred questions after your explanations but I'm gonna start slow.  When speaking in real life situations.  The ISP have given me 192.168.1.0/24 correct?

Now theoretically I could use the nets 192.168.2.0/24 and 192.168.3.0/24 if the ISP only have issued me these 3 nets correct?

But in my excercise I was only assigned 192.168.1.0/24 which is the same as the ISP only giving me that address space correct?
And thus I can't create the 192.168.2.0/24 and 192.168.3.0/24 nets for my network topology right?

When you explained that if I would use the 192.168.2.0/24 and 192.168.3.0/24 nets when I was only assigned the first net.  Then my traffic would simply collide with other companies who has been issued those nets by our same ISP correct?
And that would mean I get fired or did your explanation mean something else:confused:


I haven't read the other resonponse from The Cog yet *still reading*.
OK now I have 200 more questions after The Cog's explanations that confused me even more :-P

---

### Post by koenn on 2007-12-28
5x correct, and you would get fired for f*cking up your network design.

---

### Post by jingo811 on 2007-12-28
OK if my previous ISP summary about subnets colliding with other companies subnets using the same ISP  is truly correct.  Then I think I have a handle on things.

It's just confusing when my teacher says here's a Class C net in both scenarios when given 1 net or 3 nets.  It puts my mind into calculation mode on the 3 nets situation when it's not neccessary.
I think that is the main confusion in my head. :)

---

### Post by koenn on 2007-12-28
It's two completely separated problems. 

Example A : "you have 1 class C network. Split it in smaller subnets. " 
Example B : "You have 3 class C networks."

---

### Post by jingo811 on 2007-12-28
The ISP gave me 192.168.1.0 /24 address space for the company "Larry King Attorneys" that needs 3 nets and 20 hosts on each net.

3 nets = 2^x 
20 hosts 2^x

I chose to use 6 nets [ (2^3)-2 ] and 30 hosts [ (2^5)-2 ].


```

192.168.1.0 /24  => 192.168.1.0 /27

1100 0000 . 1010 1000 . 0000 0001 . 000|0 0000
nnnn nnnn . nnnn nnnn . nnnn nnnn . sss|h hhhh

Subnet mask = 255.255.255.224

```

```

Subnet # 0            192.168.1.0     /27
Subnet # 1            192.168.1.32    /27
Subnet # 2            192.168.1.64    /27
Subnet # 3            192.168.1.96    /27
Subnet # 4            192.168.1.128   /27
Subnet # 5            192.168.1.160   /27
Subnet # 6            192.168.1.192   /27
Subnet # 7            192.168.1.224   /27

```

```

_Subnet # 1            192.168.1.32    /27_
first host#            192.168.1.33   /27
last host#             192.168.1.62   /27

_Subnet # 2            192.168.1.64    /27_
first host#            192.168.1.65   /27
last host#             192.168.1.94   /27

_Subnet # 3            192.168.1.96    /27_
first host#            192.168.1.97   /27
last host#             192.168.1.126   /27

```

Ciscos simulation program Packet Tracer says that I have done the physical excercise 100% but when I check the detailed scores it says I have 0% when addressing the FIRST and LAST ip address for each net.  Have I calculated incorrect :confused:

_
_
_
[IMG]http://i10.tinypic.com/86o1f1h.png[/IMG]
_
_
_
_
_

---

### Post by koenn on 2007-12-28
```
Subnet # 1            192.168.1.32    /27
first host#            192.168.1.33   /27
last host#             192.168.1.62   /27
```

you have a choice of  8 subnets - you don't need to subtract 2 networks. (for host addresses you do subtract 2 addresses, because they(ll be used as network and broadcast address)

so maybe the thing expects you to use for first subnet
first host  192.168.1.1
last host  192.168.1.30

you could also solve this with 4 networks, 64 (-2) addresses each ; mask = 26 bits

but your solution would work, (so it's "physically correct" ? )

---

### Post by Kzin on 2007-12-28
> **MJN said:**
> 
Not wishing to sound like your teacher, try these:

5) Host A and Host B have addresses 171.11.15.69/27 and 171.11.15.82/27 respectively. Do they need a router between them?

6) Host A and Host B have addresses 171.11.15.71/27 and 171.11.15.98/27 respectively. Do they need a router between them?

Go on - you know you want to! ;)

Mathew

Cant add to this thread at all, except to thank koenn, Cog and MJN koz I knew how to make networks work, but not really how they work as it were.  Woot, I even went and solved quoted problems hehehe.  tnx

:KS

---

### Post by jingo811 on 2008-01-03
> **koenn said:**
> ```
Subnet # 1            192.168.1.32    /27
first host#            192.168.1.33   /27
last host#             192.168.1.62   /27
```

you have a choice of  8 subnets - you don't need to subtract 2 networks. (for host addresses you do subtract 2 addresses, because they(ll be used as network and broadcast address)

so maybe the thing expects you to use for first subnet
first host  192.168.1.1
last host  192.168.1.30

you could also solve this with 4 networks, 64 (-2) addresses each ; mask = 26 bits

but your solution would work, (so it's "physically correct" ? )

Now I see more clearly thanks!

---

### Post by jingo811 on 2008-01-17
Can somebody recommend a good VLSM excercise book with solutions?  I'm having major overlap and bad mask conflicts with my reasoning.

---

