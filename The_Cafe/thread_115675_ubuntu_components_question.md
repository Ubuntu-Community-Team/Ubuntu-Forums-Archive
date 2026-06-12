---
title: "ubuntu components question"
date: 2006-01-11
forum: The Cafe
---

### Post by pinky on 2006-01-11
Hello,
On Ubuntu their exists main, restricted, universe and multiverse.
main: free software and the core (and maintained) part of ubuntu.
restricted: non-free software

but what about universe and multiverse?
As i understand multiserve is everything you could eventually need, from free to non-free software.
About universe i have heard different statements. One said something simular like about multiverse and other said that universe is like main 100% free software but it's not continuously maintained (no guarantee of security fixes and support).
What is right? Does universe contains only free software or not?
On the ubuntu website i can read "In universe you can find almost every piece of open source software, and software available under a variety of less open licences, all built automatically from a variety of public sources."
What does "a variety of less open licences" means? For me either a licence comply with the free software definition or not.

Can someone explain this to me?

---

### Post by Burgundavia on 2006-01-11
Main - free software that is fully supported
Restricted - non-free software that is fully supported (as far as you can with closed source stuff)
Universe - free software that is community supported
Multiverse - any non-free software that can be legally distributed and is community supported.

That answer your question?

Corey

---

### Post by pinky on 2006-01-11
Thank you

[QUOTE=Burgundavia]Main - free software that is fully supported
Restricted - non-free software that is fully supported (as far as you can with closed source stuff)
Universe - free software that is community supported
Multiverse - any non-free software that can be legally distributed and is community supported.
[/QUOTE]

but why [http://www.ubuntulinux.org/ubuntu/components](http://www.ubuntulinux.org/ubuntu/components) states:
"In universe you can find almost every piece of open source software, and software available **under a variety of less open licences**"

i think this sounds a little bit confusing.
What is a "less open license"? Either their are only free software or not, i can't imaging of something which is "less free Software".

---

### Post by BoyOfDestiny on 2006-01-11
[QUOTE=pinky]Thank you



but why [http://www.ubuntulinux.org/ubuntu/components](http://www.ubuntulinux.org/ubuntu/components) states:
"In universe you can find almost every piece of open source software, and software available **under a variety of less open licences**"

i think this sounds a little bit confusing.
What is a "less open license"? Either their are only free software or not, i can't imaging of something which is "less free Software".[/QUOTE]

It is not black and white.
[http://www.opensource.org/licenses/](http://www.opensource.org/licenses/)

---

### Post by pinky on 2006-01-11
sorry for double posting, something going wrong

---

### Post by pinky on 2006-01-11
[QUOTE=BoyOfDestiny]It is not black and white.
[http://www.opensource.org/licenses/](http://www.opensource.org/licenses/)[/QUOTE]

and all this licenses meet the free software (open source) definition.
And where are the "less open licences", or what are these licenses?

---

### Post by prizrak on 2006-01-11
[QUOTE=pinky]and all this licenses meet the free software (open source) definition.
And where are the "less open licences", or what are these licenses?[/QUOTE]
As a main example you have the GPL which is completely free BUT restrictive. What that means is that all the software released under the GPL is ALWAYS open source and free for anyone to use. HOWEVER anything you build that is based on GPL software HAS TO BE released back to the community. There are licenses such as the BSD that doesn't make such a provision meaning that you can use BSD code in closed source (correct me if I'm wrong). There are licenses that might not allow free distribution of software i.e. adaware that allows you to use their software for free as long as it is not used in a corporate environment then you have to pay. There could also be restrictions such as if you want to redistribute or modify anything you have to ask for the permission of the author, even though the source could be open. A good example might be MS shared source initiative, they will give you the source code to certain things but you have to sign an NDA (non disclosure agreement) and can only use the source to improve your software when it comes to Windows integration. There are many licenses with different restrictions.

---

### Post by pinky on 2006-01-11
[QUOTE=prizrak]As a main example you have the GPL which is completely free BUT restrictive.
[/quote]

GPL is a special case of Free Software, called copyleft.
Copyleft is not about restriction, it's about protecting freedom.

> 
 There are licenses such as the BSD that doesn't make such a provision meaning that you can use BSD code in closed source (correct me if I'm wrong).


yes, but the BSD license is a license for free software too.

> 
 There are licenses that might not allow free distribution of software i.e. adaware that allows you to use their software for free as long as it is not used in a corporate environment then you have to pay. There could also be restrictions such as if you want to redistribute or modify anything you have to ask for the permission of the author, even though the source could be open. A good example might be MS shared source initiative, they will give you the source code to certain things but you have to sign an NDA (non disclosure agreement) and can only use the source to improve your software when it comes to Windows integration. There are many licenses with different restrictions.

that's all examples for non-free software (== proprietary software).

But the question remains.
What kind of "less open licences" are allowed in universe which wouldn't be allowed in main? If universe is also completly free software, like Burgundavia stated, than everything could theoretically go into main someday. But than i don't understand the sentence with the "less open licences".
So the basically question is: Does universe only contains free software and if  the answere is "yes", than why the description talks about "less open licences". Either a license qualifies itself for free software or not.

Hope someone could clear things up.

---

### Post by prizrak on 2006-01-11
Oh boy, the GPL has restrictions as far as not allowing you to close the source code. It was done to protect Open Source sure but it IS a restriction. There are many different open source licenses and they have different terms, GPL is completely free other licenses are not as free. Like I mentioned before a good example would be a license that gives you the source code but in order to change something you must get the manufacturers permission. This is a "less open license" as compared to the GPL which is considered to be the "main" fully open license. That is what they mean it's software that is released as free/open but the licensing does not allow you to do anything you want with it (like the GPL).

---

### Post by pinky on 2006-01-13
[QUOTE=prizrak] Like I mentioned before a good example would be a license that gives you the source code but in order to change something you must get the manufacturers permission. This is a "less open license"...[/QUOTE]

OK, this kind of licenses you describe are neither "Open Source" nor Free Software.
If this kind of software is allowed in universe we can stop the discussion with the result that universe contain free and non-free software. Terms like "less open licenses" just confuse the people. As i have said before, their is no "less open" either the software license is conform with the DFSG, than it is free software or it istn't conform than it isn't free software. There exist nothing like "a little bit free software".

---

