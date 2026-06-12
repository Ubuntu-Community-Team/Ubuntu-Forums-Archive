---
title: "Vware permission mess-up!"
date: 2008-06-10
forum: Virtualisation
---

### Post by benc123 on 2008-06-10
Hello,
I was trying to set up a new virtual machine in VMware, it told me i could not because i was not the owner.

Being new to Ubuntu i just ran it in the terminal with 'sudo' in front.

This worked but after a while it crashed, due to my over worked laptop.

Now i cannot open VMware without running it in terminal as 'Root'.

I know this is my own fault for being hasty but i cannot seem to be able to fix it.

It seems that the problem is in '.VMware' then 'preferences', as it says 'root' is the owner, not me.

I would really appreciate any help in this matter as i do not wont to have to run it in 'root' every time.
Thanx benc.

---

### Post by fjgaude on 2008-06-10
If it is the .vmware file, then that should be you as the owner. Do this:

```
sudo chmod -R 755 /home/<you>
sudo -R <you>:<you> /home/<you>
sudo 644 /home/<you>/.vmware
```

That should fix this issue and let's hope it's the only one. <smile>

---

### Post by benc123 on 2008-06-10
Thanx, i thought of that as soon as i had written the post!! Im so dum!

Now back to the original problem.

I do not have permissions to create a new virtual machine.

How can i change the permissions so i can?

i cant seem to find the right file to change, or really know what to do with it! lol.

Thanx benc

---

### Post by fjgaude on 2008-06-10
Gosh, I don't know what to say... you must have taken a wrong turn when you installed vmware, eh?

One time, as I recall, I had to run the console from root to get to an already made vm. After I got to it then I could get back normally without doing **sudo vmware**.

You might try that.

---

