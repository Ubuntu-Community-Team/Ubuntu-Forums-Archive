---
title: "Remove visual feedback from GUI password dialogues"
date: 2008-07-14
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2008-07-14
Since the developers don't seem too keen on [my proposal to *add* visual feedback to CLI password dialogues](http://ubuntuforums.org/showthread.php?t=214393), and a lot of Ubuntu users seem to believe this to be a security feature (supposedly someone standing behind you can see how many characters are in your password), why not keep it consistent?

1. Consistency of interface keeps new users from being confused.

2. It either is a security feature or it isn't. If it really is a security feature, why half-*** security by making the terminal "secure" and making the GUI not secure?

If you're for this, vote it up:
[Idea #11136: Remove visual feedback from GUI password dialogues](http://brainstorm.ubuntu.com/idea/11136/)

---

### Post by olskar on 2008-07-15
And here is the brainstormidea about adding visual feedback to CLI password dialogues:

[http://brainstorm.ubuntu.com/idea/11118/](http://brainstorm.ubuntu.com/idea/11118/)

Personally I vote for that instead

---

### Post by aysiu on 2008-07-15
> **olskar said:**
> And here is the brainstormidea about adding visual feedback to CLI password dialogues:

[http://brainstorm.ubuntu.com/idea/11118/](http://brainstorm.ubuntu.com/idea/11118/)

Personally I vote for that instead
Been there. Done that.

I just think this half-assed implementation is stupid.

It either is a security issue or it isn't.

If it is a security issue, there's no reason to keep visual feedback in the GUI. If it isn't a security issue, there *should* be visual feedback at the command-line.

---

### Post by aysiu on 2008-07-15
> **olskar said:**
> And here is the brainstormidea about adding visual feedback to CLI password dialogues:

[http://brainstorm.ubuntu.com/idea/11118/](http://brainstorm.ubuntu.com/idea/11118/)

Personally I vote for that instead
Been there. Done that.

I just think this half-assed implementation is stupid.

It either is a security issue or it isn't.

If it is a security issue, there's no reason to keep visual feedback in the GUI. If it isn't a security issue, there *should* be visual feedback at the command-line.

---

### Post by smartboyathome on 2008-07-15
> **aysiu said:**
> Been there. Done that.

I just think this half-assed implementation is stupid.

It either is a security issue or it isn't.

If it is a security issue, there's no reason to keep visual feedback in the GUI. If it isn't a security issue, there *should* be visual feedback at the command-line.

I don't think it is a security issue, and also voted to add CLI password visual recognition. I was freaked out when I first came to Linux and saw that it wouldn't show my password when typing sudo (that is what my first post was about, actually :lolflag:), and think that if we do this the other way around we would get even more of those types of posts. :(

---

### Post by aysiu on 2008-07-15
> **smartboyathome said:**
> I don't think it is a security issue No, it's not. But peeople keep *saying* it is, which is why I started the other Brainstorm idea. The lack of visual feedback in the terminal makes no sense from a usability standpoint. Yes, that's the way it's always been, but that's not the way it always has to be.

---

### Post by Wolki on 2008-07-15
> **aysiu said:**
> The lack of visual feedback in the terminal makes no sense from a usability standpoint. Yes, that's the way it's always been, but that's not the way it always has to be.

Exactly. While it may be a minor security issue (you can actually see the number of characters in the password if someone types slowly), having them is much nicer for usability (like not being confused when you do it for the first time, or being able to see the number of characters you typed to check when you have the feeling you hit an additional key but are not sure, or being able to clear the entry field easily when you did make a typing mistake without having to hope that you hit backspace often/long enough).

That said, in most cases you can substitute the graphical dialog for the terminal-based one, and on a server the security issue may be more of an issue since they are more often accessible remotely.

And many linux-users tend to be very conservative toward changes in how their operating system works, so such a change would likely incite a lot of heated discussion. And because of that, I doubt it would be changed upstream, so it would be another ubuntu-only change that has to be maintained for newer versions. I doubt that makes much sense for a use case the developers are actively trying to get rid of (having to enter your password in a terminal)

I fully agree that it would make more sense to always show them. But I understand the developers taking a pragmatic stance here. :-/

---

### Post by aysiu on 2008-07-15
I don't really have a problem with the developers' stance at all. They've basically said it's too much trouble to change, which is fine.

I just don't like people pretending it's this "security feature" that must be kept that way lest someone find out how many characters are in your password.

---

### Post by drubin on 2008-07-15
I agree. Still confuses me when entering passwords on the CLI. Like to know that what i am typing is going through..

---

