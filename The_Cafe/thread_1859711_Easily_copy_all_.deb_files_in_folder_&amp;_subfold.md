---
title: "Easily copy all .deb files in folder &amp; subfolder via cli?"
date: 2011-10-14
forum: The Cafe
---

### Post by mips on 2011-10-14
Hi,

I need to copy all *.deb files found in /media/Ubuntu 11.10 amd64/pool/main to /var/cache/apt.

Problem is they are spread across a gazillion sub folders inside 'main'.

Is there an easy way to do this via cli? Can someone provide me with the commandline syntax please?

Why? I'm doing a custom install of 11.10 starting with a base (cli only) install and then I want to build on that but I have limited bandwidth so would prefer to copy all the deb files from the cd into the apt cache so any files that are local will install faster and save me some bandwidth.

---

### Post by nerdopolis on 2011-10-14
I think its
```

find -path  "/media/Ubuntu 11.10 amd64/pool/main" -name "*.deb" | while read FILE
do
cp "$FILE" "/var/cache/apt"
done
```

---

### Post by mips on 2011-10-14
Thanks, tried that but it did nothing.

---

### Post by matt_symes on 2011-10-14
Hi[FONT=monospace]
[/FONT]
```
sudo bash -c "find /media/Ubuntu\ 11.10\ amd64/pool/main -name *.deb -exec cp {} /var/cache/apt \;"
```Here is a 1 liner.

Kind regards

---

### Post by ice60 on 2011-10-14
find "/media/Ubuntu 11.10 amd64/pool/main" -type f -name '*.deb' -exec cp -i {} "/var/cache/apt" \;

i think that is correct. maybe wait for someone to say it's correct first though because i'm not sure!

---

### Post by mips on 2011-10-14
> **matt_symes said:**
> Hi[FONT=monospace]
[/FONT]
```
sudo bash -c "find /media/Ubuntu\ 11.10\ amd64/pool/main -name *.deb -exec cp {} /var/cache/apt \;"
```Here is a 1 liner.

Kind regards

Thanks a million, works brilliantly!


> **ice60 said:**
> find "/media/Ubuntu 11.10 amd64/pool/main" -type f -name '*.deb' -exec cp -i {} "/var/cache/apt" \;

i think that is correct. maybe wait for someone to say it's correct first though because i'm not sure!

Thanks, looks the same as the above.

---

### Post by Martin Marshalek on 2011-10-14
EDIT: Sorry, just re-read your post.

---

### Post by mips on 2012-05-02
Thanks again, this info just saved my bacon one more time ;)

---

### Post by blithen on 2012-05-02
The thread has been solved but had to chime me 2 cents in.
This is why I LOVELOVELOVELOVELOVE the terminal...so powerful.

---

### Post by mips on 2012-09-06
And I came back looking for it again :biggrin:

---

### Post by graabein on 2012-09-06
The terminal is where you execute little programs that are all created to solve some small task, and they're constructed to take input stream and create output stream, while printing info to the screen, usually. So you just string em together and whoopdedo.

---

