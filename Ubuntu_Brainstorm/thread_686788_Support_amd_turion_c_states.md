---
title: "Support amd turion c states"
date: 2008-02-03
forum: Ubuntu Brainstorm
---

### Post by jpittack on 2008-02-03
I have filed a bug report here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188739]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188739")

Because it is not Ubuntu's fault, its not really a bug.  After reporting it, I thought this would be the better place to post.

I bought my laptop with the idea that I would be getting excellent battery life, due to all of these c states and cool n' quiet.  Only cool n' quiet works.  In both windows and ubuntu I have these problems.  Lower battery life, tons of heat, fan is blowing hot air nonstop.

I called my vendor and got the worst answer I think I could ever receive.

"AMD processors are a cheap processor and if you had chosen intel you would not have these problems.  If you would like to upgrade to the 9 cell battery..."

I wanted to cry.  I bought amd because it is better than intel in terms of the processor (core 2 duo computer was 500 more at the time and I knew I would not see if a difference).

I visit the gentoo forums, and that is where I first found out about this problem.  My dsdt file shows that the processor section is empty.  I can't attach it due to invalid file type.  It is in dsl

To make matters worse, if dynticks in enabled, the c1 state is disabled.  Thats why my hardy install draws two more watts of power at idle.  Under this idea, I should be saving up to 8 watts of power with dynticks working properly and c states working properly.  Thats almost half the power I am using right now!  Talk about a double in battery life!

To make matters worse, My graphics card is not supported by the radeon driver, and using the fglrx driver causes problems.  I am stuck with vesa, not recieving any power savings.

I know I don't have the worst situation, but this is ridiculous!  AMD has been talking about their new processors helping push past the 5 hour battery life limit.  I could already be there!

Now that I feel a bit better,  Could a neighborly ubuntu delepover make this happen?  Or atleast help me modify my dsdt file so that everything works.

---

