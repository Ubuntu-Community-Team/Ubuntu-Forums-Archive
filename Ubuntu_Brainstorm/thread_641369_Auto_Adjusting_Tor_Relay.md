---
title: "Auto Adjusting Tor Relay"
date: 2007-12-15
forum: Ubuntu Brainstorm
---

### Post by AlexEagar on 2007-12-15
During the Ubuntu installation there should be a check box labeled 'Enable Auto Adjusting Tor Relay.' This check box should be checked by default. There should be a tool tip that explains that running a tor relay helps to preserve the freedom of speech around the world. Ubuntu should then be smart enough to automatically enable and disable the relay based on the network configuration of the computer. It would for example run when connected to broadband Internet, but not when connected to dial-up Internet. It might also need to determine whether it was already behind an censoring firewall.

I think that there are a lot of people who like the idea of running a Tor relay but are worried about high network usage or being incorrectly viewed as a criminal sympathizer. If this option was checked by default they would be assured that they are part of a large crowd which are all using this technology and thus they would worry less about the Tor relay using too many network resources or about being incorrectly viewed as a criminal sympathizer. The desktop users would also be able to claim ignorance by stating that they just installed their OS with the default settings.

The Tor relay would need to be auto adjusting if it were to be enabled by default. It would automatically determine network capabilities and limit its own network activity to a relatively very low level to prevent it from throwing up red flags to network administrators.

---

### Post by 23meg on 2007-12-15
I don't think it's a good idea to push Tor to people this way. You'd have a hard time explaining people where more than half of their bandwidth is going when they use Ubuntu. The desktop CD installer is intended for a non-technical audience, and including this option that people won't be capable of evaluating properly, and will likely bypass, isn't a good idea.

Tor's developers have actually requested that it be removed from Ubuntu, the reason being that it's developed very fast, and keeping it in a release that's supported for 1.5 to 5 years isn't a good idea, because it will give users a false sense of anonymity. Afterwards, an Ubuntu developer volunteered to keep Tor packages in Universe up to date, so IIRC an exception was granted for Tor to be kept up to date as long as it doesn't break anything, and it's still in Hardy. I'm not sure it's exactly up to date in all stable releases, and its presence in Ubuntu depends on the work of one volunteer at the moment. 

Your suggestion would entail moving Tor to the main component from Universe, and installing it by default, which would mean officially supporting it, and I suspect that to support it at the quality standards expected of software in main would be a tough job. I also don't see a chance that it could get the same kind of exception in main.

Tor isn't a complete anonymity solution, and shouldn't be advertised as such. If you'd like more people to be aware of and use it, which still is a laudable goal, I'd suggest working towards integrating it better with Ubuntu's default applications, helping keep it up to date, and introducing it to a subset of Ubuntu users who'd more directly benefit from what it offers, and be more likely to contribute to it.

---

### Post by AlexEagar on 2007-12-15
> **23meg said:**
> I don't think it's a good idea to push Tor to people this way. You'd have a hard time explaining people where more than half of their bandwidth is going when they use Ubuntu.

That's why I suggested that the default setting would be to use very few network resources. A few resources spread across a large audience would provide a lot of resources.

> **23meg said:**
> The desktop CD installer is intended for a non-technical audience, and including this option that people won't be capable of evaluating properly, and will likely bypass, isn't a good idea.

It would be auto adjusting so that it's not noticed by the non-technical audience.

> **23meg said:**
> Tor's developers have actually requested that it be removed from Ubuntu, the reason being that it's developed very fast, and keeping it in a release that's supported for 1.5 to 5 years isn't a good idea, because it will give users a false sense of anonymity. Afterwards, an Ubuntu developer volunteered to keep Tor packages in Universe up to date, so IIRC an exception was granted for Tor to be kept up to date as long as it doesn't break anything, and it's still in Hardy. I'm not sure it's exactly up to date in all stable releases, and its presence in Ubuntu depends on the work of one volunteer at the moment.

I didn't realize that they had reservations with it being installed by default. I'm not saying that it's ready the way it is, but if it worked the way I described, I think that it could greatly increase the network capabilities of Tor.

> **23meg said:**
> Tor isn't a complete anonymity solution, and shouldn't be advertised as such. If you'd like more people to be aware of and use it, which still is a laudable goal, I'd suggest working towards integrating it better with Ubuntu's default applications, helping keep it up to date, and introducing it to a subset of Ubuntu users who'd more directly benefit from what it offers, and be more likely to contribute to it.

I'm not advocating the use of the Tor client by default because I actually think that would be harmful in that people would download large files using it and it would bog down the system. My recommendation is limited to an auto adjusting relay server being enabled by default to increase Tor network capabilities by lowering the inhibitions and fears people have about running a Tor relay server.

---

### Post by 23meg on 2007-12-15
[QUOTE=AlexEagar]That's why I suggested that the default setting would be to use very few network resources. A few resources spread across a large audience would provide a lot of resources.[/QUOTE]

[QUOTE=AlexEagar]It would be auto adjusting so that it's not noticed by the non-technical audience.[/QUOTE]

Per-application bandwidth throttling is somewhat tricky. It won't work as intended in all scenarios, and deploying it by default to hundreds of thousands of machines whose users won't be aware of how it works, what it intends to do, how it can be fixed if it acts erratically, etc. will be tricky too. The only app I know that does it, which incidentally is called Trickle, is pretty buggy, and will cause 100% CPU usage with many software.

[QUOTE=AlexEagar]I didn't realize that they had reservations with it being installed by default. I'm not saying that it's ready the way it is, but if it worked the way I described, I think that it could greatly increase the network capabilities of Tor.[/QUOTE]

They didn't have reservations with it being installed by default; they had reservations with it being in the repositories at all. Installing it by default would be another story (see my edited first post).

---

### Post by AlexEagar on 2007-12-15
> **23meg said:**
> Per-application bandwidth throttling is somewhat tricky. It won't work as intended in all scenarios, and deploying it by default to hundreds of thousands of machines whose users won't be aware of how it works, what it intends to do, how it can be fixed if it acts erratically, etc. will be tricky too. The only app I know that does it, which incidentally is called Trickle, is pretty buggy, and will cause 100% CPU usage with many software.

The relay server already has throttling built into it, so I don't think that that in and of itself would be a huge problem. It would just need a way to determine the current Internet settings and adjust accordingly. I don't think that users would get upset about it unless they noticed a problem. I was just reading on their web site that if you are behind a NAT, you have to set up port forwarding, so that would need to happen automatically. So the relay server may to be to the point where it needs to be quite yet, but if we get it to that point it, I think it would be useful to have it enabled by default. Of course I suppose there's the possibility that the Tor Project might find lots of servers with very light loads to be more trouble than they are helpful because of the constant connecting and disconnecting they would cause, but if they thought they would be useful, I think it would be great. Honestly it's probably not realistic any time soon, but it would be a cool and useful feature at some point.

> **23meg said:**
> They didn't have reservations with it being installed by default; they had reservations with it being in the repositories at all. Installing it by default would be another story (see my edited first post).

I understood what you said, I just used the wrong phrase as I quickly wrote my reply. I meant to say that I didn't know that they had reservations about including it.

---

### Post by AlexEagar on 2007-12-15
And as a quick clarification about the poll question; the question is not whether you think the option should be included during the install.

The question is, if it was enabled by default during the install, would you leave it enabled?

---

### Post by AlexEagar on 2007-12-18
Here is some info about how the Tor Project wants to increase the amount of people running relay servers. My idea doesn't really fit with their current plans but I can imagine them changing their plans at some later point in their development. But I stand by my solo 'Yes' vote; that if the relay was enabled by default, I would leave it enabled.

---

### Post by AlexEagar on 2007-12-18
Oops, I forgot the links.

[https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#head-895c260589199718c6001722afdeb22bf41929d6](https://wiki.torproject.org/noreply/TheOnionRouter/TorFAQ#head-895c260589199718c6001722afdeb22bf41929d6)

[https://www.torproject.org/svn/trunk/doc/contrib/incentives.txt](https://www.torproject.org/svn/trunk/doc/contrib/incentives.txt)

---

