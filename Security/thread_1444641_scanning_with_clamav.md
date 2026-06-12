---
title: "scanning with clamav"
date: 2010-04-01
forum: Security
---

### Post by amite on 2010-04-01
i am using clamav for virus protection,when i scanned my windows partition with clamscan it shows list of threats but doesn't removeit.How can i remove those threats?

i am new to ubutnu,so please tell me if any better antivirus available for both ubuntu and wndows............

---

### Post by km0r3 on 2010-04-01
> **amite said:**
> i am using clamav for virus protection,when i scanned my windows partition with clamscan it shows list of threats but doesn't removeit.How can i remove those threats?


Well, the sole fact that it's a Windows partition [...] :lol:

To remove the files you only have to pass the `--remove` option.

For example:
```
clamscan --remove <other_opts>
```Actually, be aware of **false positives**. ClamAV recognized some of the scripts I wrote myself as threats, which was definitely false, so be careful with passing the --remove option if you don't want important files to be accidentally deleted.


> 
i am new to ubutnu,so please tell me if any better antivirus available for both ubuntu and wndows............I mostly use [f-prot]("http://www.f-prot.com/") if I have to do a Virus check, which is almost never the case; to not forget that I use crond.

I think ClamAV does just fine, though.

[SIZE=4]But please browse the forums... there are maybe 500+ threads with the phrase "antivirus" in the topic line (?!), which may help you any further. :)[/SIZE]

---

### Post by amite on 2010-04-01
> Actually, be aware of **false positives**.

then  would it  be better to remove those threats manually by use of "rm -f" 

or can do anything better?

---

### Post by km0r3 on 2010-04-01
> **amite said:**
> then  would it  be better to remove those threats manually by use of "rm -f" 

or can do anything better?

I don't know if it would be better. I'm no security expert, but there are some here in the forums AFAIK who *do* now.

It would be a lot more work for you to delete each file manually, but if you trust ClamAV, if not I suggest you to manually securely delete the file with a tool like `shred` or `srm`.

---

### Post by amite on 2010-04-03
when i scanned a windows drive, results showed some trojans.......Actually that is text file.So i think trojan are attached with that text file and i don't want delete that text file.

 is there any way to remove that trojan without deleting the text file.

i am a student and learning so excuse me if thing i asked seems weird............

---

### Post by km0r3 on 2010-04-03
> **amite said:**
> when i scanned a windows drive, results showed some trojans.......Actually that is text file.So i think trojan are attached with that text file and i don't want delete that text file.

 is there any way to remove that trojan without deleting the text file.

i am a student and learning so excuse me if thing i asked seems weird............

If the Trojan is attached to your text file why don't simply open it with an editor and copy the parts you want to save and save that to a new file.

I don't think it will do any harm to try that.

If it's a very important file and the file is hardly damaged you can still use a tool like* hexdump*.

Good luck.
[B]
No warranty.[/B]

---

### Post by amite on 2010-04-03
> **km0r3 said:**
> If the Trojan is attached to your text file why don't simply open it with an editor and copy the parts you want to save and save that to a new file.

I don't think it will do any harm to try that.

If it's a very important file and the file is hardly damaged you can still use a tool like* hexdump*.

Good luck.
[B]
No warranty.[/B]

thnx, 
idea is better for text file and hexdump is good one in case of pictures or other small file.But what if virus is attached with some large files such .pdf or etc.In this case it is not possible to use hexdump.#-o

any command or s/w available which works as de-binder(!!!)???:mad:

---

### Post by km0r3 on 2010-04-03
> **amite said:**
> 
any command or s/w available which works as de-binder(!!!)???:mad:

I doubt there's something like that (for free). I read about "Good Anti-Trojan" software for Windows systems, but I can't judge either that they're good or if they do what you want them to do.

Think it requires some basic understanding of malware, and all I know for sure about it that it has been written by a person and it's nothing more than a sequence of 0's and 1's :) .

I hope you get your data back :)

---

