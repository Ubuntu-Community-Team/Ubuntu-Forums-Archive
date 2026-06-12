---
title: "[SOLVED] Please explain why people don't like this brainstorm idea!"
date: 2008-03-06
forum: Ubuntu Brainstorm
---

### Post by unimatrix on 2008-03-06
**idea #3368: Install LILO in case Grub installation fails** [[link]("http://brainstorm.ubuntu.com/idea/3368/")]

I simply do not understand why this idea is getting down-voted. It is a fairly simple solution to making sure new users aren't immediately repelled from Ubuntu because of a grub installation failure.

I know 3 people who said 'linux sucks' because grub failed to install and went back to Windows forever.
Is THAT what the brainstorm community wants?!?

There is absolutely no excuse for not implementing this, so can someone please explain what kind of madness makes people click the down arrow?

---

### Post by Mr. Picklesworth on 2008-03-06
My theory is that a visible group of people are voting down ideas they do not understand. Lots of technical ideas that require reasoning beyond what a title can manage seem to wind up at the bottom of the list...

The mention of kernel updates bother in the comments is a reasonable one, though it could (*should*) be tidily managed by an extra layer of abstraction (generic boot loader update program) that the update scripts work through.

---

### Post by unimatrix on 2008-03-06
Interesting theory. It's probably valid, at least for a portion of users.

I've been thinking further though. It could simply be because they think it would be easier to fix this 3-year-old bug:
[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/14135)
I wonder why it still hasn't been fixed. It's marked as critical, so dunno. If they can't fix it in time for Hardy, it would be nice to use Lilo as a backup plan.

---

### Post by aysiu on 2008-03-06
Is there reason to believe that if Grub fails to install that Lilo will be successful?

---

### Post by unimatrix on 2008-03-06
Well, it worked for me when grub failed on my server. Also, the bug is a grub-installer specific problem. I think it has something to do with not understanding UUIDs correctly.

---

### Post by aysiu on 2008-03-06
> **unimatrix said:**
> Well, it worked for me when grub failed on my server. Also, the bug is a grub-installer specific problem. I think it has something to do with not understanding UUIDs correctly.
But then wouldn't the solution be to fix the bug in the Grub installer, instead of falling back to Lilo?

---

### Post by unimatrix on 2008-03-06
Yes, obviously, it would.
But the bug hasn't been fixed in 3 years, why would it be before Hardy is released? Just concerned a bit... We are talking about an LTS here.
On the other hand, it would be really simple to add a little backup plan to run the lilo installer if grub fails.

---

### Post by aysiu on 2008-03-06
> **unimatrix said:**
> Yes, obviously, it would.
But the bug hasn't been fixed in 3 years, why would it be before Hardy is released? Just concerned a bit... We are talking about an LTS here.
On the other hand, it would be really simple to add a little backup plan to run the lilo installer if grub fails.
But realistically, if they aren't going to fix the Grub bug, why would they go to the trouble to program in a fallback mechanism?

---

### Post by nutz on 2008-03-06
Grub has become the defacto standard. Too many options can sometimes be a bad thing. Especially for new users.

---

### Post by unimatrix on 2008-03-06
@aysiu: Well, technically it's a grub-installer bug. And my point is that there wouldn't really be a lot of trouble to do this.

@nutz: I agree with you. And I like Grub too, but I also like things that work. But the (new) user doesn't really know Grub is being installed (which is the way it should be), so he wouldn't need to know there was a fallback to Lilo either. It's just better to install Lilo, than not to install anything.

---

### Post by Mr. Picklesworth on 2008-03-07
I suppose another issue definitely being prodded at here is how installing Lilo as a fallback is a really horrible workaround / kludge type of thing. It would be better if one of them just worked for us 100% of the time, and that one method does not for something as important as the boot loader shows us some serious bugs need fixing at the source ASAP.

---

### Post by unimatrix on 2008-03-07
I guess I'm going to have to agree.
I'll edit the idea to somehow redirect attention to fixing the bug.

---

