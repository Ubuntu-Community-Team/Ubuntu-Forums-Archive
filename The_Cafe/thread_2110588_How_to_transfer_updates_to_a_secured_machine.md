---
title: "How to transfer updates to a secured machine"
date: 2013-01-30
forum: The Cafe
---

### Post by linmick on 2013-01-30
Hello, I have a question to ask and I hope to be understood correctly. 

**_ My Background:_**

I have a Computer that I have designated as an invention Machine. That is a machine where I have started to Prototype my ideas. I'm hoping to eventually submit them a company. The Machine in questions has been put off Cloud Computing (indefinitely) in other words the internet. In order to protect my ideas in case the Computer gets compromised because of the Cloud. Yes, I know  it has a highly configured Firewall, A  Network Firewall, A great Linux Operating system powered by Kubuntu / Ubuntu family, A Root Scanner. However because of the sensitive nature to protect my ideas before I get to benefit from them. I can't afford any security  lapse into the Cloud.

**_A Bit More Details / Question:_**

   The Machine in question runs a 64Bit Kubuntu 12.04 LTS (Stability intentional due to such nature). 


    I need a couple of opinions from individuals whom are more knowledgeable than myself on this. 

[*] If possible how would you have pushed patches to such a machine?

  Again, I would have skipped the Updates for security but I'm sure they are not just for "security" but also safe LTS stability improvement patches to the operation of the software on the machine.

[*] If I were to setup an identical Software installation by using the "Muuon installed packages option" on the Confidential machine. Later  copying that installed packages file to the  "none secret machine" to duplicate. Later anytime the none secret machine has an update just copy the  debs in: /var/cache/apt through a medium to the "Confidential machine" I think personally that is tedious. Although, in name of safety I'm willing to go through that if possible. Suggestions, ideas?







:popcorn:  After I make profit(s) donate to the Open Source community for making such a great OS.

---

### Post by anaconda on 2013-01-30
Scroll down 2/3 of this page:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

There are some instructions regarding your problem.
I would use the apt-offline solution.

---

### Post by linmick on 2013-01-31
Anaconda, Thank you very much I'll have a look at it right now. ):P




> **anaconda said:**
> Scroll down 2/3 of this page:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

There are some instructions regarding your problem.
I would use the apt-offline solution.

---

### Post by mips on 2013-01-31
This is the part you wanna look at [https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)


Personally I think there is a greater chance of a company stealing your ideas when you present it to them than being hacked.

---

### Post by linmick on 2013-02-03
Mips, Thank You for your thoughtful reply as well. Actually, I'm trying to make up my mind with the Company. I thought about Innovating before but never tried it while growing up.  I thought the Invention process itself is very complicated. Actually choosing the right company to help me with my idea has proven to be even more complex.  I have read so much on them I could always not use them and instead go to the top. The thing is I'm not proficient in the things that they are supposed to help me with. That is why in the first place  I need them since I'm not a Patent Lawyer, a  Engineer and trying to avoid a costly mistake. Truth be told I have heard of  Inventors/Innovators getting hurt by Snake Oil Salesman sadly.

> **mips said:**
> This is the part you wanna look at [https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)


Personally I think there is a greater chance of a company stealing your ideas when you present it to them than being hacked.

---

### Post by mips on 2013-02-04
> **linmick said:**
> Mips, Thank You for your thoughtful reply as well. Actually, I'm trying to make up my mind with the Company. I thought about Innovating before but never tried it while growing up.  I thought the Invention process itself is very complicated. Actually choosing the right company to help me with my idea has proven to be even more complex.  I have read so much on them I could always not use them and instead go to the top. The thing is I'm not proficient in the things that they are supposed to help me with. That is why in the first place  I need them since I'm not a Patent Lawyer, a  Engineer and trying to avoid a costly mistake. Truth be told I have heard of  Inventors/Innovators getting hurt by Snake Oil Salesman sadly.

My one friend sold a financial plan to a insurance company but before he even showed it to them he had a legal contract drawn up (which in itself cost a small bundle of money) they had to sign. Dealt with things like NDA, restraint and retention of intellectual property should the company get sold etc. The firm got brought out by a bigger player, they changed the layout a bit, stopped paying him royalties and he is now involved in a 3yr long legal battle. He won his first case against them and fortunately they saw he was not simply gonna roll over and take it and they are now in settlement talks wrt the second case.

It's a dog eat dog world out there with no morals/integrity so make sure you got all bases covered.

---

### Post by Paqman on 2013-02-04
You might want to consider setting up a local mirror and allowing your quarantined machine access to that.

If you're feeling really paranoid and want to completely isolate that machine then you could still sneakernet the packages over to it from another machine. Dumping the content of /var/cache/apt/archive onto a USB stick will allow you to update any of the packages that the two machines have in common (which will be a lot). Or else use one of the abovementioned solutions.

However, I think you might be making things a bit hard for yourself. Would not simply encrypting the sensitive data on the "innovation" machine be a more elegant and practical solution?

---

### Post by alphacrucis2 on 2013-02-04
On the dog eat dog world. I recall reading that a kid sent an idea to Apple to add some improvement to ipods. Apple's lawyers wrote back demanding that she cease and desist. I guess because the lawyers advised that she might be able to demand royalties if Apple implemented something similar. Weird world we live in. Bottom line - when you approach the company or backer - that you have contractual arrangements locked down. Unfortunately this may means you need a lawyer.


Yeah - here's the article:

[http://cgull8m.hubpages.com/hub/Apple-Sends-3rd-Grader-Cease-And-Desist-Letter](http://cgull8m.hubpages.com/hub/Apple-Sends-3rd-Grader-Cease-And-Desist-Letter)

---

