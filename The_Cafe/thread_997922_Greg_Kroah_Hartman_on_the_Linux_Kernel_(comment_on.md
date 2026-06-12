---
title: "Greg Kroah Hartman on the Linux Kernel (comment on canonical included)"
date: 2008-11-30
forum: The Cafe
---

### Post by simtaalo on 2008-11-30
good talk about the kernel development process which includes some interesting comments about canonical

[http://www.youtube.com/watch?v=L2SED6sewRw](http://www.youtube.com/watch?v=L2SED6sewRw)

---

### Post by simtaalo on 2008-12-01
nobody watched this?

during the talk he puts up a list of organisations that contribute most to the linux kernel, on that list canonical is around 300th, and he says that canonical hardly contributes anything back.

this comment made me think that i would be better off moving distro as i'd prefer to be using something which was more part of the wider linux community.

this isn't to say i don't like ubuntu, its a great distro, and i think its a great bridge when moving from windows to linux.

---

### Post by Icehuck on 2008-12-01
I thought he said they aren't on the list because they contribute absolutely nothing. Though I was listening to it while cleaning up the house so I might have not heard it properly.

---

### Post by ibutho on 2008-12-01
I think he said that Canonicals contribution to kernel development was very minimal. Some said he was biased because he works for NOVELL, but I personally don't think this has anything to do with it.

---

### Post by jomiolto on 2008-12-01
Thanks, I'm watching it right now, and it seems really interesting from a programmer's point of view.

---

### Post by Luke has no name on 2008-12-01
I still don't understand how we don't contribute when all our changes are open source. The only way we could possibly NOT contribute is to not make kernel changes PERIOD, which I know we do.

---

### Post by ibutho on 2008-12-01
> **Luke has no name said:**
> I still don't understand how we don't contribute when all our changes are open source. The only way we could possibly NOT contribute is to not make kernel changes PERIOD, which I know we do.

My understanding is that he did not say Canonical does not contribute. He said that their contributions to the kernel were eclipsed even by volunteer projects like Debian and Gentoo. Some companies like Red Hat, Mandriva, NOVELL etc, employ people to work full time on kernel development. I am not sure if canonical does the same.

---

### Post by Sealbhach on 2008-12-01
So when I download updates in Ubuntu, are we saying that most of those updates have been created by Debian?

Also, I have trouble understanding what they mean by "upstream" and "downstream", if anyone could clarify.



.

---

### Post by wmcbrine on 2008-12-01
I've always seen Ubuntu/Canonical as contributing more to the desktop experience -- something that's at least as important as the kernel.

---

### Post by eentonig on 2008-12-01
I'm not that familiar regarding Canonicals contributions, but my impression is/was that Canonical has more focus on GUI and user perception and less on pure kernel development.

In that context, I'm not at all that surprised that they have such a low 'score' from a kernel development point of view.

---

### Post by ibutho on 2008-12-01
> **Sealbhach said:**
> So when I download updates in Ubuntu, are we saying that most of those updates have been created by Debian?

Also, I have trouble understanding what they mean by "upstream" and "downstream", if anyone could clarify.



.

Ubuntu is based on Debian Unstable, so a lot of stuff in Ubuntu is from the Debian project. This means that Debian is upstream relative to Ubuntu (and Ubuntu is downstream because it is using another distributions work). The same applies to packages e.g. Xorg is upstream to all distros because its provided by a third party project that is not directly related to the distros.

---

### Post by Icehuck on 2008-12-01
> **Sealbhach said:**
> So when I download updates in Ubuntu, are we saying that most of those updates have been created by Debian?

Also, I have trouble understanding what they mean by "upstream" and "downstream", if anyone could clarify.



.

A good portion of the patches you download are patches from Debian. 

When they say "upstream" they are referring to the source of the code. In this case they are referring to the Linux kernel developers. When they are saying "downstream" they are referring to the users/distributions.  

When it comes to the kernel they are saying that Canonical doesn't give back to the source. They take an existing kernel, say 2.6.16, and modify that to suit their needs. If they find bugs in that version they don't report them or submit possible fixes for it.

---

### Post by simtaalo on 2008-12-01
> **wmcbrine said:**
> I've always seen Ubuntu/Canonical as contributing more to the desktop experience -- something that's at least as important as the kernel.

that is a fair point. what major things have been done by canonical on gui terms which had not been done by other distro's?

---

### Post by simtaalo on 2008-12-01
> **Icehuck said:**
> 
When it comes to the kernel they are saying that Canonical doesn't give back to the source. They take an existing kernel, say 2.6.16, and modify that to suit their needs. **If they find bugs in that version they don't report them or submit possible fixes for it**

doesn't the bit i've bolded seem quite wrong?

---

### Post by jomiolto on 2008-12-01
Okay, it was indeed an interesting glimpse at the kernel development process and gave a nice idea of huge the whole thing is. That video also reminded me that there's no need for me to be running the stock Ubuntu kernel, and I can very well compile my own from the latest source -- if I can just figure out all the stuff I need to compile in it (hmm, there's another thing on my list of things to do during the hols ;) )...

Also, that comment about Canonical only committing six patches (if I heard correct) is certainly thought-provoking. I wonder how much they commit to other projects, such as all the bell and whistles included in a Gnome desktop environment? I'd say that it is rather worrying, given the success of Ubuntu, *if* they do not commit much of anything back to the projects.

---

### Post by simtaalo on 2008-12-01
> **jomiolto said:**
> Also, that comment about Canonical only committing six patches (if I heard correct) is certainly thought-provoking. I wonder how much they commit to other projects, such as all the bell and whistles included in a Gnome desktop environment? I'd say that it is rather worrying, given the success of Ubuntu, *if* they do not commit much of anything back to the projects.

yup that's the issue that made me start the thread. however i didn't think about the point made of how much canonical may contribute into other aspects of the system.

i would be interested to know how much canonical does contribute to these other aspects.

> **jomiolto said:**
> Okay, it was indeed an interesting glimpse at the kernel development process and gave a nice idea of huge the whole thing is

the figures on how much code is changed everyday is mind-boggling.

---

### Post by Delever on 2008-12-01
I have seen this presentation a while ago, and enjoyed it alot. He said that canonical "does not give back to community", and indeed i would like it not to be the case. However.

I haven't payed much attention to this comment back then, but now, that OP brought it up, I can't help but bite:

Isn't "free for everyone" to "use as they wish", part of the beauty of open source? If so, then all you can do is to point fingers, like "geez, he is not helping, only using!". But well, nowadays most users are using and not actually helping to build software, and everyone seems fine with that.

It could be said that canonical is not real user, only distributor, but that would be like wishing to have rules on how your free software is distributed and mentioned; of course, in open source world, you can either envy the ones who become successful, or beat them by making better product.

So instead of pointing "they do not deserve credit" fingers it may be worth to look what canonical actually did. Canonical may have had advantage of "some" additional startup income, but ubuntu came out of distribution soup as something different and new, with simple but strong idea, simple but strong goal, simple but stable name and theme.

In my humble opinion.

---

### Post by xArv3nx on 2008-12-01
> **Sealbhach said:**
> **So when I download updates in Ubuntu, are we saying that most of those updates have been created by Debian?**

Also, I have trouble understanding what they mean by "upstream" and "downstream", if anyone could clarify.



.
Absolutely.

---

### Post by Namtabmai on 2008-12-01
> **simtaalo said:**
> nobody watched this?

during the talk he puts up a list of organisations that contribute most to the linux kernel, on that list canonical is around 300th, and he says that canonical hardly contributes anything back.

this comment made me think that i would be better off moving distro as i'd prefer to be using something which was more part of the wider linux community.

this isn't to say i don't like ubuntu, its a great distro, and i think its a great bridge when moving from windows to linux.

Absolutely. In fact I think I'm going to tell my boss tomorrow to fire our secretary. I mean, all she does all day is answer calls/mail/email forward them to the right department, make sure that other can get on with their work without needless interruption and makes sure the correct and full information/problems go to the right department. It's not like she actually **does** anything for the company directly.

:rolleyes:

---

