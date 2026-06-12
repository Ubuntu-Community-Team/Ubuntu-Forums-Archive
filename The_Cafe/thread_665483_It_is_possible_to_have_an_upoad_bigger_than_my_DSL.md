---
title: "It is possible to have an upoad bigger than my DSL sincronization?"
date: 2008-01-12
forum: The Cafe
---

### Post by Kosimo on 2008-01-12
If my router synchronizes to my ISP at 700 kbps (upload)
What does it means if using some programs like azureus I can reach better upload speeds? Like 100 KB/s  (800kbps)  

It is technically possible to have a better upload than my my own DSL sincronization speed?

Usually should be a bit less than the maximum right?

Thanks!

---

### Post by hhhhhx on 2008-01-12
I could be wrong, but I think that azourez is using download not upload.  And if you are uploading torrents at higher that your maximum consider youself very lucky

---

### Post by Kosimo on 2008-01-12
> **xhhux said:**
> I could be wrong, but I think that azourez is using download not upload.  And if you are uploading torrents at higher that your maximum consider youself very lucky

Of course azureus is downloading as well...
But that speed I'm talking about is upload speed of course ;)

I feel lucky, but I'm trying to understand how is possible to reach a better speed than my router synchronization.

---

### Post by popch on 2008-01-12
It's a bit difficult to tell from here. If your apparent upload rate is higher than the rate promised by your ISP, that could mean one or more of several things:

[LIST]
[*]The rate is in actual fact faster than it has to[/LIST][INDENT][LIST]
[*]because your ISP has added some margin of error or some reserve because that's cheaper than handling customers' complaints about traffic being too slow
[*]or your ISP has not sold all of his bandwidth and some of it reaches current customers[/LIST][/INDENT][LIST]
[*]The speed is only apparently faster than the promised one[LIST]
[*]because your recipient (Azureus) uses other cirteria for measurement
[*]or they are simply mistaken.[/LIST][/LIST]Comparing the thoughput of any transmission is always tricky if not done by the same people and/or to the same standard. 

Part of that difficulty starts with the conversion between bits per second and bytes per second. Anyone knows that one byte is eight bits, of course. Only it's not true. On your disk, for instance, one byte occupies most probably ten or more bits, and some kinds of RAM use nine bits. 

Then, there's the 'overhead' of using a telecommunication line. In order to transmit - say - a file of 100MB, you move much more over the line, and even then there are moments when you are not moving anything at all. I would suspect that the overhead of a simple file transfer on the internet might be something like 10 to 30 per cent.

Conclusion: your ISP appears to deliver on his promise for the upload rate. Be happy and content.

---

### Post by Kosimo on 2008-01-12
> **popch said:**
> It's a bit difficult to tell from here. If your apparent upload rate is higher than the rate promised by your ISP, that could mean one or more of several things:

[LIST]
[*]The rate is in actual fact faster than it has to[/LIST][INDENT][LIST]
[*]because your ISP has added some margin of error or some reserve because that's cheaper than handling customers' complaints about traffic being too slow
[*]or your ISP has not sold all of his bandwidth and some of it reaches current customers[/LIST][/INDENT][LIST]
[*]The speed is only apparently faster than the promised one[LIST]
[*]because your recipient (Azureus) uses other cirteria for measurement
[*]or they are simply mistaken.[/LIST][/LIST]Comparing the thoughput of any transmission is always tricky if not done by the same people and/or to the same standard. 

Part of that difficulty starts with the conversion between bits per second and bytes per second. Anyone knows that one byte is eight bits, of course. Only it's not true. On your disk, for instance, one byte occupies most probably ten or more bits, and some kinds of RAM use nine bits. 

Then, there's the 'overhead' of using a telecommunication line. In order to transmit - say - a file of 100MB, you move much more over the line, and even then there are moments when you are not moving anything at all. I would suspect that the overhead of a simple file transfer on the internet might be something like 10 to 30 per cent.

Conclusion: your ISP appears to deliver on his promise for the upload rate. Be happy and content.

Thank you so much for your explanation.

I'm agree about what you're saying about my ISP promises.. 

But, when I say synchronization, I mean the real sync that my router have to my ISP.  

So if my router says I've got an 602 kbps (upload)

How can I reach a better speed? Due to some kind of data compression?
Or the bite translation as you said

---

### Post by popch on 2008-01-12
I am not overly familiar with the inner workings of a DSL connection or modem. I only use and pay for one.

In the good old times when you used POTS (plain old telephone service) with analog modems, you could apparently exceed the bandwidth of your line by applying compression. You had not to do anything in order to do that because reasonably recent modems did that all by themselves.

DSL works over the same lines and is still subject to some of the same constraints. Therefore, I expect the DSL modems to perform quite a complex set of functions in order to maximise the actual bandwidth, i.e. the rate at which you transmit your data. 

I don't think that there's anything you can do in order to increase that bandwidth. You can always try and save bandwidth by not using the internet for other tasks while uploading. 

There are other parameters which you can try tuning, but some of those are either precluded or already provided by the protocols and service providers you use. Packet size and compression come to mind, as well as choosing a time of the day when the internet itself is not overly congested.

By the way, you keep bringing up the term 'synchronisation'. According to my admittedly limited understanding of DSL and modems, I do not think that this term is applicable to this topic, i.E. I do not think that there are any systems or components which actually are synchronised (run in lockstep).

---

### Post by bufsabre666 on 2008-01-12
i get that on my 384kbps cable connection

i should max at 48 but i get 60 regularly

same with download when the sources are closer i can go over my 4mbit

its because theres always slack in the line, when other people around you with the same service arent using it you can theoretically take their bandwidth

---

