---
title: "What is the next kernel we can expect ?"
date: 2009-04-23
forum: The Cafe
---

### Post by BGFG on 2009-04-23
Going into update withdrawal here. At this point i'll take anything....
So where do we go to ? .29 or .30 ?
I've read that these offer even more speed. If that is possible :)

---

### Post by SomeGuyDude on 2009-04-23
I'm on .29 now. Is nice. Lotta big updates.

---

### Post by chucky chuckaluck on 2009-04-23
i can never tell the difference. it's like trying to figure out which lightning bug is the fattest.

---

### Post by Daisuke_Aramaki on 2009-04-23
first thing you should do is to see the release notes at kernel.org. they are well detailed. i am running 2.6.30-rc3 and no big problems yet.

---

### Post by LookTJ on 2009-04-23
```
uname -r
```

prints kernel release version

---

### Post by DougieFresh4U on 2009-04-23
I'm using the .30rc3, can't use 'fglrx' like I was with the .28 kernel.:(

---

### Post by MaxIBoy on 2009-04-23
I'm on 2.6.29.1 (custom compile,) and it's working okay for me. However, odd-numbered releases are "unstable," so the next "stable" release will be 2.6.30.

---

### Post by FuturePilot on 2009-04-23
> **MaxIBoy said:**
> I'm on 2.6.29.1 (custom compile,) and it's working okay for me. However, odd-numbered releases are "unstable," so the next "stable" release will be 2.6.30.

The kernel stopped going by the even odd scheme a while ago.

---

### Post by MaxIBoy on 2009-04-23
> **FuturePilot said:**
> The kernel stopped going by the even odd scheme a while ago.Thought they'd taken it back up again for minor releases?

---

### Post by FuturePilot on 2009-04-23
> **MaxIBoy said:**
> Thought they'd taken it back up again for minor releases?

Nope, the unstable versions end in rcX where X is some number. The latest unstable version is 2.6.30-rc3

---

### Post by MaxIBoy on 2009-04-23
I stand corrected, thanks.

---

### Post by BGFG on 2009-04-24
I look forward to .30 then. Especially now that i know that the sufix -k will re-compile my nvidia kernel module, rather than me re-installing the entire thing. yeah, i used to do that :)

About what ? another month perhaps ?

---

### Post by BGFG on 2009-04-24
[http://www.linux-mag.com/id/7308/1/](http://www.linux-mag.com/id/7308/1/)

Now I NEED the -30 kernel..

---

### Post by LightB on 2009-04-24
> **BGFG said:**
> [http://www.linux-mag.com/id/7308/1/](http://www.linux-mag.com/id/7308/1/)

Now I NEED the -30 kernel..

Why? Do you run big arrays or something? If not, ext4 will probably be better overall for desktop use for a while because of stability. Btrfs isn't even complete, thus far.

---

### Post by BGFG on 2009-04-24
> **LightB said:**
> Why? Do you run big arrays or something? If not, ext4 will probably be better overall for desktop use for a while because of stability. Btrfs isn't even complete, thus far.

Check the last part of the article. To test the fs and help the development cycle along. Obviously it won't be my default fs, but creating formatting 450+ gig partition in 1 sec is something i'd like to experience for myself.

---

### Post by xir_ on 2009-04-24
> **BGFG said:**
> Check the last part of the article. To test the fs and help the development cycle along. Obviously it won't be my default fs, but creating formatting 450+ gig partition in 1 sec is something i'd like to experience for myself.

only if it's intentional

---

### Post by Slug71 on 2009-04-24
2.6.31

---

### Post by shadylookin on 2009-04-24
say what you will but I'm still waiting on the hurd kernel:P

and waiting and waiting and waiting

---

### Post by MaxIBoy on 2009-04-25
You'll be waiting a long time-- the FSF is exploring the possibility of ditching HURD in favor of another microkernel like coyotos.

---

### Post by oomingmak on 2009-04-25
> **MaxIBoy said:**
> the FSF is exploring the possibility of ditching HURD in favor of another microkernel like coyotos.


It doubt that it will be Coyotos.
>   In April 2009, Jonathan Shapiro announced that "Active work on Coyotos stopped several months ago, and is unlikely to resume. I have no current plans to continue the Coyotos work"[http://www.coyotos.org/pipermail/bitc-dev/2009-April/001791.html](http://www.coyotos.org/pipermail/bitc-dev/2009-April/001791.html)

HURD just goes from strength to strength - lol.

---

### Post by wolfen69 on 2009-04-25
> **MaxIBoy said:**
> I'm on 2.6.29.1 (custom compile,) and it's working okay for me. However, odd-numbered releases are "unstable," so the next "stable" release will be 2.6.30.

that is no longer true. the numbers don't mean anything as far as stability.

---

