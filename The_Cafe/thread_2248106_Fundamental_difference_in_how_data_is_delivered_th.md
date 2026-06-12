---
title: "Fundamental difference in how data is delivered through TV and internet"
date: 2014-10-12
forum: The Cafe
---

### Post by user1397 on 2014-10-12
Someone asked me the about this recently and I couldn't come up with an answer on the spot.  He asked what is so different between the way a TV show for example is delivered through your television and how it would stream over the internet.  He asked, why is it that there is always buffering and loading when it comes to loading anything on the internet, yet we've had this technology for over 50 years which seems to load content instantaneously, even when live.  

What am I missing?  His argument is sound, why are we opting to use a method of delivery which at least from an outside perspective seems to be a lot slower and more annoying than the established TV method

Now, obviously the internet is a complex beast compared to television and you can do much more on it and it has a multitude of protocols associated with it, I am simply talking about delivering media content such as movies and TV shows.

---

### Post by pqwoerituytrueiwoq on 2014-10-12
TV is a broadcast, you select the frequency to view the content
when you stream it it is per request, it is not being sent to every computer on the Internet you are asking a server for something and it is giving it to you (anyone else who request it), where as a tv is receiving everything (by everything i mean 95% garbage) at all times

---

### Post by pfeiffep on 2014-10-12
+1> **pqwoerituytrueiwoq said:**
> [B]TV is a broadcast, you select the frequency to view the content
when you stream it it is per request[/B], it is not being sent to every computer on the Internet you are asking a server for something and it is giving it to you (anyone else who request it), where as a tv is receiving everything (by everything i mean 95% garbage) at all times
Adding to this - TV broadcast has no notion of quality of reception - if there's an interruption in the signal received there's no filling in the missing information as it's simply lost.
Contrasting this with streaming to a computer which has quality of reception established  - there is a two way communication path established between the sender and receptor.

---

### Post by bab1 on 2014-10-12
> **pfeiffep said:**
> +1
Adding to this - TV broadcast has no notion of quality of reception - if there's an interruption in the signal received there's no filling in the missing information as it's simply lost.
Contrasting this with streaming to a computer which has quality of reception established  - there is a two way communication path established between the sender and receptor.

Adding a little more...  Unlike the TV broadcast, the stream via the Internet is not constant.  It is a series of packets.  There is no guarantee that all the packets use the same route from the sender to the recipient.  The order received is also not guaranteed.  The recipient reassembles the packet sequences if they arrive out of order.  There is lots of overhead to stream video and audio over the Internet that is not there for broadcast TV.

---

### Post by grahammechanical on 2014-10-12
The buffering is necessary so that the viewer does not need to wait until the next packet has been downloaded. Think of TV as radio with pictures. If we do not have our TVs switched on and tuned to the channel/station we miss the broadcast. With Internet steaming the video file is waiting on a server until we choose to download and watch it.

Ask your friend to answer this question. Why do we have DVD discs when we have TV, which has been around for, how many decades did he say? Then he can work out the answer to his own question. Why have TV when we have movies? Didn't films come first?

Regards

---

### Post by mips on 2014-10-13
> **grahammechanical said:**
> 
Ask your friend to answer this question. Why do we have DVD discs when we have TV, which has been around for, how many decades did he say? Then he can work out the answer to his own question. Why have TV when we have movies? Didn't films come first?


:confused: I don't see how that is related to the op's question.

---

### Post by buzzingrobot on 2014-10-13
Different technologies intended to serve different purposes.

Radio and TV are broadcast technologies. Electromagnetic waves are transmitted that can be acquired by anyone with an antenna and re-converted to sound and images via the appropriate hardware.  Cable TV -- transmission via a wire -- is a variation that avoids atmospheric interference with broadcasts.


The design of the internet was premised on a desire for communication and collaboration, not on a desire to build a platform for distribution of TV-like content.  Content on the net is not broadcast.  It is downloaded, on request, to each individual IP address that is the source of the request. The complexities of how that content gets from a server to your screen is another matter.

---

### Post by user1397 on 2014-10-17
Thanks for the replies guys, I definitely understand the differences a lot better now.  Cheers.

---

### Post by prisoner8492 on 2014-10-17
Good responses.

To draw an overly simplified and semi-sound analogy:
TV = UDP (packets are sent, no confirmation of delivery)
Internet = TCP (packets must be confirmed with the server)

---

### Post by DuckHook on 2014-10-18
Great technical explanations above. I'm going to risk one that's a little more on the philosophical side.

The internet was designed to be an empowerment medium. It does so by allowing us to interact with each other. That is it's raison d'etre, it's founding tenet, and it's most precious virtue. It ought to be the ultimate enablement and equalization tool because it is designed for give and take: the two-way dialogue that constitutes real communication. At its best, it allows us to express ourselves, like we are doing right now on this very thread in this very forum. Even when streaming, the internet shares many qualities of the best books: you read it at your own pace, can pause in the middle, give yourself the time to ponder its message or its meaning, even look something up, or bring up an opposing point of view. It is mind-expanding.

TV, in stark contrast is, if not exactly an emasculating medium, then at least a disempowering one. It precludes interaction. Its raison d'etre is to force feed content into the minds of passive receptacles. It is disabling and unequal because, by its nature, it can only work if dominated by massive content producers and broadcasters. It is a one-way process that mocks the meaning of "communication" because it neither cares to, nor indeed can sustain a dialogue. Until the advent of PVRs it could not be viewed at your own pace, could not be paused, gave no time for reflection or second thought, and therefore left no room for critical thought or opposing points of view. It is mind-numbing.

These contrasting mediums with diametrically opposed goals will give you some idea why TV can stream without interruption (it was designed with exactly this goal and nothing but this goal in mind) whereas the internet cannot. In fact, the concept of a buffer is actually a very ingenious kludge that was invented to make a medium that is essentially interactive accommodate a streaming function that is not natural to it.

If you look at the internet this way, you can understand why so many internet advocates and defenders are livid at the actions of the carriers that dominate its infrastructure. Since most of them are cable or telecom giants, they wish to change the internet from its naturally dialogue-enhancing, interactive and empowering nature into just another vehicle for mindless passive content streaming. They have largely succeeded. Most people these days think of the internet as just something that delivers music streams, videos and Netflix, and rarely if ever consider its higher purpose.

---

### Post by sam-c on 2014-10-18
try livestation works on debian and ubuntu with fast adsl of course:p:p

---

### Post by prisoner8492 on 2014-10-18
Duckhook's a lot more optimistic about the Internet than I am. The more enjoyed the net during the late 90's, prior to the advent of social media, widespread streaming media, and Web 2.0 in general. Content was only published by those who had the intelligence and determination to pay for web hosting and learn HTML. It was "natural selection" that filtered out the crackpots, newbs, and every soapbox carrier with an opinion

---

### Post by DuckHook on 2014-10-18
I understand where you're coming from, but I have no problem with soapbox orators, crackpots or newbs. Especially newbs. I was once a newb, and I treasure the help that I received from those selfless souls who took the time and trouble to show me the ropes. May they continue to live in blessedness and joy.

I would rather deal with the riff-raff than regress to a world in which all of our voices were mute. I grew up in that world and, looking back at it, there was very little to recommend it in comparison to what we have today.

My ire continues to be reserved for the cartels that want to turn us into passive little receptacles for whatever junk they want to shove down our throats.

I'm in danger of hijacking this thread. Hope the mods will forgive the digression from an old curmudgeon.

---

### Post by Elfy on 2014-10-27
posts jailed - keep politics out of it, thanks

---

