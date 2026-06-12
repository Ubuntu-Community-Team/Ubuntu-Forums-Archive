---
title: "How many punch cards to distribute Ubuntu"
date: 2008-05-02
forum: The Cafe
---

### Post by Peter09 on 2008-05-02
OK,
as a lead on from this thread

[http://ubuntuforums.org/showthread.php?t=778304](http://ubuntuforums.org/showthread.php?t=778304)

how many punch cards would it need to distribute Hardy?

PC

---

### Post by RazorEdge on 2008-05-02
More than a little and less than too many.

---

### Post by amingv on 2008-05-02
Say not such things!
(I can't imagine booting the "Live Punchcard" from there)

---

### Post by Peter09 on 2008-05-02
Yes - the forums would be full of problems such as -

I've installed Hardy, but have found three cards left on the floor, what should I do?

PC

---

### Post by tamoneya on 2008-05-02
well an IBM 5081 has 80 rows with 8 columns according to wiki which translates to 80 bytes. The smallest ISO is the 32 bit server at 525 MB.
525*1024*1024/80 = 6881280

---

### Post by amingv on 2008-05-02
> **Peter09 said:**
> Yes - the forums would be full of problems such as -

I've installed Hardy, but have found three cards left on the floor, what should I do?

PC

Sit back and wait for the kernel panic, or the undefined reference to <function>.

On the bright side, anyone with a paper puncher and some masking tape could easily tune the kernel.

---

### Post by yssida on 2008-05-02
I believe it has to be 525*1,000,000/8 since it's in MB and not MiB. I'm not sure though.

---

### Post by popch on 2008-05-02
You would have to reserve some columns (bytes) of each card for a sequence number.

On the other hand, the 'traditional' IBM punched card (with 80 columns) has twelve rows (holes) in each column, if I remember it correctly. If you have a programmable card reader you can place one and a half byte in each column.

Does anyone know the thickness of a card?

---

