---
title: "cryptsetup passphrase not accepted after upgrade"
date: 2014-04-11
forum: Server Platforms
---

### Post by SundaY82 on 2014-04-11
I did an long overdue upgrade of my ubuntu server and installed alot of updated packages.
Now I can't decrypt my raid anymore, 

# cryptsetup luksOpen /dev/sdh raid
Enter passphrase for /dev/sdh: 
No key available with this passphrase.

Passphrase copied from text file just like before upgrade, not typed on keyboard.

I think it has to do with the passphrase containing a special character(swedish ö).
Other encrypted volumes with normal characters can be decrypted just fine after upgrade.

root@xxx:~# uname -a
Linux xxx 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686 athlon i686 GNU/Linux

Upgraded packages: [http://paste.ubuntu.com/7237049/](http://paste.ubuntu.com/7237049/)

Some cryptsetup output: [http://paste.ubuntu.com/7237080/](http://paste.ubuntu.com/7237080/)

locale output: [http://paste.ubuntu.com/7237131/](http://paste.ubuntu.com/7237131/)

I have tried many things to get it to decrypt but all has failed so far.

In desperate need of assistance, 4TB of data I would really not like to loose.

---

### Post by frostschutz on 2014-04-11
If you are sure you have the correct passphrase, there are only that many charsets to try... (supply your own -t charset)

```
echo -n 'yøurp&#333;ssphröse' | iconv -f utf8 -t iso8859-13 | cryptsetup luksOpen /dev/thing luksthing
```

If your cipher was something with whirlpool, there was an update recently that caused backward compatibility issues. But doesn't seem to be the case, so it's your passphrase you have to work on...

If it's only a single character in question, bruteforce would also be an option. less than 100k tries for arbitrary 1-2 byte squences in place of that character.

---

### Post by SundaY82 on 2014-04-12
Whoho, BIG THANKS!

Your first solution worked perfectly.

Now I just need to replace this passphrase with one without a special char.

---

### Post by SundaY82 on 2014-04-12
Hmm, running cryptsetup luksAddKey /dev/thing it asks for the existing passphrase, same problem as before.
Using your above syntax to convert to iso and pass to cryptsetup but just changing the last bit from luksOpen to luksAddKey didn't work.
I just got the prompt back and no new key added.

---

### Post by frostschutz on 2014-04-12
in case of luksAddKey, I don't know if it expects the echo to be the old or the new key... you might have to add --key-file=- or something. and if that does not work either, you might have to echo > somefile and then use --key-file=somefile instead.


also I should have mentioned before, the echo solution leaks your passphrase to your bash history and to the process list. On a live cd that usually does not matter, but if you're in a multi user environment, it might.

---

### Post by SundaY82 on 2014-08-11
Waking an old thread.

In my attempt to add a new key without special character I seem to have f***ed up badly. 
Now I cant decrypt it with previous working method.
If I dump luks now there is a key added to slot 1 and 2. Before I had only slot 0 populated, this one is empty now. Not sure what I have done to be honest. But I'm pretty sure I just played with this one character.

The brute force method that was suggested, would someone be kind and give a script that would help me accomplish this?

---

### Post by frostschutz on 2014-08-11
If you don't know what you've done, how is anyone supposed to help you?

In order to remove a key slot, you have to give a working key or passphrase for one of the other slots. So you should know what is in at least one of these key slots you added.

Brute force any way you like, very simple example:

```

for a in your yöur yoür
do
    for b in pass päss
    do
        for c in phrase phräse phr&#257;se
        do
            echo -n "$a$b$c" | cryptsetup luksOpen /dev/thing thing
        done
    done
done

```

---

### Post by SundaY82 on 2014-08-11
Ok thank you, I will see if I can remember what I did... messed with it a couple of month ago and restart server last night to find out that my previous solution doesn't work any more.

---

