---
title: "Suggestions to improve Jockey"
date: 2009-05-14
forum: The Cafe
---

### Post by stwschool on 2009-05-14
Personally I like Jockey. It's a very reliable and simple way of getting a job done. It has a couple of flaws however that could do with ironing out.

1. Lack of visual feedback
I like how you can open the terminal box when using gdebi or synaptic to see what the installer is doing. It serves two purposes, it provides reassurance that it's doing something, and if it dies you have a rough idea where and why. Jockey does not. If something goes wrong the process is.. click activate, wait ages on 0% and then it craps out with a non-helpful error message.

2. Better handling of slow internet
Jockey dies when I try to use it from my mobile phone's internet but works perfectly when I do it from the internet at work which is fast. The reason, I suspect, is that Jockey gets no response from the backend which is busy downloading a huge file on slow internet, so it thinks it's died, and so it craps out. It needs to handle this more gracefully, indeed point 1 would probably solve that issue, so rather than have the program assume that as the backend hasn't made contact stuff has died, the user can make their own informed choice to shut it down and try again later.

3. Make sure all repositories carry the same driver
The Thai one doesn't. I did a tech post on here yesterday because I could get the driver listed off the install CD, but not once installed. It turned out that the problem was that I'd forgotten to switch from our flaky Thai server to the US ones used from the CD. If repositories aren't up to scratch, kick them off the network (the Thai one also causes problems with updates, synaptic installs, etc).

---

