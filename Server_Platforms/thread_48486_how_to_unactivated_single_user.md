---
title: "how to unactivated single user"
date: 2005-07-12
forum: Server Platforms
---

### Post by ihot on 2005-07-12
dear all,

how to unactivated single user on ubuntu, i always used single user if i forget the password. but on the second thought it's not save for my pc. i'm affraid if someone change my passwd used single user facillilty. mmm... it makes me wondering is it include disadvantage when i using linux. well people said that linux is more secure than mic'soft... need answer and help here... thank u so much.  :)

---

### Post by tomchuk on 2005-07-12
Disable the recovery option in /boot/grub/menu.lst and set up a grub password. Disable boot from CD in the BIOS and set a BIOS password. That should take care of the most obvious vectors of attack.

If you cannot physically secure your computer, there is ultimately nothing you can do. Given physical access, even a chimp can own your box in a matter of minutes with a couple google searches and a liveCD.

---

### Post by ihot on 2005-07-14
which one? cause to many recovery word in menu.lst. do i must erase all sentence contain recovery? sorry i'm newbie here. or in title (line 104) do i must put "#" in front sentence contain recovery?

thank you

---

### Post by tomchuk on 2005-07-14
To set a password, uncomment the password line at the beginning and change the password. Optionally, read into creating an md5 password for grub for added security.

To disable the recovery option, look for the lines:

```

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

```

and change the last line to
```

# alternative=false

```
Don't uncomment it - it is a configuration directive for update-grub, which you should run next:
```

sudo update-grub

```

Instead of disabling single user mode, which can be useful, you could alternatively set lockalternative to true, which will password protect single user mode.

---

### Post by ihot on 2005-07-21
thank you Tom. GBU.

---

