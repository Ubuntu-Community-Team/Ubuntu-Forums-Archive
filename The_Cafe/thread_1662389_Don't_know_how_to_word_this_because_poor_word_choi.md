---
title: "Don't know how to word this because poor word choice causes confusion."
date: 2011-01-08
forum: The Cafe
---

### Post by sinclair86 on 2011-01-08
I realized that my definition of DHCP was not the same as the people responding to my original thread. I wasnt using the word in the literal sense of the definition I was using it as an applied idea. Kinda like saying "That's the ****." **** could be the literal term meaning there is the poop  or it could mean (as an applied idea) that's cool. So its obvious I dont know how to ask what I want to know. Instead of asking what I want to know I will tell what I want to know. If some how I am still unclear please ask questions before answering.

I want to know what stops me what stops me from using my neighbor's network without having access to his local network. For the time being lets leave firewalls out of the equation.

---

### Post by saulgoode on 2011-01-08
> **sinclair86 said:**
> I want to know what stops me what stops me from using my neighbor's network without having access to his local network. For the time being lets leave firewalls out of the equation.
My preliminary analysis concludes that your not having access to your neighbor's network plays a significant role in preventing you from using it.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-01-08
> **sinclair86 said:**
> I want to know what stops me what stops me from using my neighbor's network without having access to his local network.

Your inherent respect for other people's property?

---

### Post by GregBrannon on 2011-01-08
> I want to know what stops me what stops me from using my neighbor's network without having access to his local network. For the time being lets leave firewalls out of the equation. 

While you seem to have reasonable familiarity with the English language, your question is practically nonsensical.  One can 'assume' what you're trying to ask - what you want to know - but rather than requiring the audience to waste a bunch of time guessing, why don't you try again?

You've essentially asked what prevents you from using something you don't have access to.  I'm sure you can clarify.

---

### Post by koenn on 2011-01-08
> **saulgoode said:**
> My preliminary analysis concludes that your not having access to your neighbor's network plays a significant role in preventing you from using it.

I concur.

---

### Post by Megaptera on 2011-01-08
Does your neighbour's ISP allow this sharing or are you breaching Terms and Conditions. Even though you two are content sharing - I assume your neighbour knows? - you could fall foul of the ISP.

---

### Post by Ranko Kohime on 2011-01-08
Well, here's my stab at it.

You're trying to access your neighbors' wireless network, but you don't have access to the wired portion.

There's two sides to this coin.  If you have permission, ask the neighbor if he can assist you in getting set up, as he might be using encryption (which is always a good idea to use on any wireless network), or he might have MAC (Media Access Control, the address of your network hardware, not to be confused with the IP address) address control, in which case he would have to add your computer to the list in his router.

If you don't have permission, and either of the aforementioned points are true, you're SOL.  Look elsewhere for your Internet connection.

---

### Post by CharlesA on 2011-01-08
If you are doing this without your neighbor's permission, what you are attempting to do is illegal. If you have their permission, then it's fine.

Judging from the content of both of your threads, it seems like you don't have their permission.

I'll leave this open for now, but it will be watched.

---

### Post by juancarlospaco on 2011-01-08
On the previous, dhcp has nothing to do with it, ipv6 dont need dhcp, and geolocation and internet works anyways.

If you want to use neighbor's  wifi, you need their encrypted password, or a chainsaw.

---

### Post by sinclair86 on 2011-01-09
Ugh! Its very frustrating not being understood. I dont know if it stems from my lack of explanation or a readers lack of understanding to what I am saying. I am not trying to do anything illegal here I am only trying to get help seeing what I am missing from my narrowed vision.

Let me try to paint a picture. 

There are 3 components I see when I look at a network. one is the source. second is the destination. the last would be everything in between.

If I picture the source (my ISP) to be a giant router, the destination (my house) should have a "ethernet cord" plugged directly into it (i Know there are multiple switches/hubs/routers between its not just a straight line but for the sake of the discussion lets assume that it is a straight line.) If I am not alone on the network (network meaning same ISP with the same services). what is to stop me from being my neighbor or him me?


@GregBrannon lol yea you were right. I went back and read what I wrote and, by the way that I worded it, only I actually knew what I was saying.

---

### Post by CharlesA on 2011-01-09
It doesn't work like that. Each connection is identified by either the MAC address (Cable) or by using something like PPPoE (DSL). The ISP assigns your cable/dsl modem an ip address based on that information.

Each connection to the ISP is dedicated, so you aren't really on the same network as your neighbor.

To fully understand how it works, you'd have to read up on subnetting and how it relates to networking.

---

### Post by CharlesA on 2011-01-09
It doesn't work like that. Each connection is identified by either the MAC address (Cable) or by using something like PPPoE (DSL). The ISP assigns your cable/dsl modem an ip address based on that information.

Each connection to the ISP is dedicated, so you aren't really on the same network as your neighbor.

To fully understand how it works, you'd have to read up on subnetting and how it relates to networking.

---

### Post by sinclair86 on 2011-01-09
> It doesn't work like that. Each connection is identified by either the MAC address (Cable) or by using something like PPPoE (DSL). The ISP assigns your cable/dsl modem an ip address based on that information.

Each connection to the ISP is dedicated, so you aren't really on the same network as your neighbor.

To fully understand how it works, you'd have to read up on subnetting and how it relates to networking.

womp womp. This is why Im horrible at trying to find what I am looking for by asking others. I spend too much time trying to clarify what I mean. If one pictures a local network (from in house, router downwards) would it not be a just a miniature model of of a much larger network, say my ISP? If I am able to manipulate my local network why can't it carry up the ladder? 

Let me try it this way.

Say say the ISP is the router and each home, it connects to, is a computer. What stops me from faking to be different computer than I am?


If MAC address (on the modem) is what does it (what was being brought up in the other thread) thats all I wanted to know this whole time and thats what was being stated in the other thread.

---

### Post by Paqman on 2011-01-09
Consider your landline phone. What stops you from receiving your neighbour's calls or making calls from their number? The fact that the phone company routes calls addressed for the right recipient to the right destination.

Similarly, your neighbour's packets are addressed to them, they never get routed to you. If you were literally on the same network that might mean that your hardware simply ignored packets not addressed to you, but due to the large amount of hardware in between you and any other user they in fact never even get sent to you. While conceptually you are on the "same network" if you go far enough up the food chain, so is everybody else since the internet is just a network of networks. That doesn't mean everybody sees each other's packets.

---

### Post by CharlesA on 2011-01-09
Paqman pretty much hit it on the head.

Does it make a bit more sense now?

---

### Post by GregBrannon on 2011-01-09
In response to unkind criticism of another's misuse and abuse of the English language, a wise man once said here, "People don't come here to learn English."  Since you admit difficulty communicating concepts with others with whom you may not share a common vocabulary, I'll suggest that you try to ask questions in terms most people would understand.  In this case, as Paqman suggests, I think you're asking, "Why don't I get my neighbor's network traffic just as I don't get the mail addressed to his house, calls to his phone, or his email?" or "Why doesn't he get mine, etc?"

An answer in the same terms is, "Even though you and your neighbor may use the same internet service provider, cell phone company, email provider, postman, etc., you each have unique addresses, so you each receive only the messages addressed to you."

You can study this as deeply as you'd like from your keyboard.  You might start with Wikipedia, but I'm sure there are other great internet resources that explain network addressing to the degree you require.

---

### Post by sinclair86 on 2011-01-09
Ugh!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Its never once had it not made sense. What I ask and how I say it is so that you are giving me your responses not the I want you to give me. But it clear that there is mis communication somewhere. Just close this thread because it will just keep going around in circles.

@GregBrannon I know not how to communicate with others. I spend most of my time dedicated to school and isolation in my room.

---

### Post by GregBrannon on 2011-01-09
> **sinclair86 said:**
> 
@GregBrannon I know not how to communicate with others. I spend most of my time dedicated to school and isolation in my room.

Practice.

---

### Post by Elfy on 2011-01-09
> Just close this thread because it will just keep going around in circles.


I'll close this then.

To be honest - it looks to me like you are trying to ask a question without asking a question. 

Bear in mind that not everyone has english as a mother tongue - and making a 'question' vague will, and obviously has, lead to misunderstanding.

Now I am English, english is my mother tongue - I have absolutely no idea at all what your last post means ...

---

