---
title: "Two keys for newly installed full disk encryption?"
date: 2022-03-18
forum: Security
---

### Post by efjen on 2022-03-18
Hello!

I just installed Kubuntu 21.10, and chose the encrypted LVM option during installation. It now asks me for the passphrase on boot, as expected.

However, I see something that scares me: cryptsetup luksDump reports TWO keys for the encrypted partition. I guess one of them is the passphrase I supplied, but what is the other one?

(I removed the salt from the output I pasted below. Not sure if that was necessary or not, I am not well versed on this.)


```

Ke*****s:
  0: luks2
        Key:        512 bits
        Priority:   normal
        Cipher:     aes-xts-plain64
        Cipher key: 512 bits
        PBKDF:      argon2i
        Time cost:  4
        Memory:     923333
        Threads:    1
        Salt:
        AF stripes: 4000
        AF hash:    sha256
        Area offset:32768 [bytes]
        Area length:258048 [bytes]
        Digest ID:  0
  1: luks2
        Key:        512 bits
        Priority:   normal
        Cipher:     aes-xts-plain64
        Cipher key: 512 bits
        PBKDF:      argon2i
        Time cost:  4
        Memory:     1015869
        Threads:    1
        Salt:
        AF stripes: 4000
        AF hash:    sha256
        Area offset:290816 [bytes]
        Area length:258048 [bytes]
        Digest ID:  0

```

---

### Post by TheFu on 2022-03-19
There are 8 slots (0-7) for decryption keys.  This is just for the header. The actual encrypted data was/is encrypted using keys that are unknown to  us users.

Use the **cryptsetup** tool to get all the information available about the encryption container.  The manpage is quite excellent too, so rather than me searching there for an answer (I haven't looked), could you?
Use either **man** or **xman** to see the cryptsetup manpage.  It will provide all the available information that anyone here would know.

---

### Post by efjen on 2022-03-20
Thanks for your reply.

The reason I came across the two keys to begin with, was because I was looking into how to change the passphrase using cryptsetup. I have now done the following test:

1) cryptsetup luksAddKey /dev/sda4 to add another passphrase. The device now has three key slots in use.
2) Check if the machine can be booted using the new passphrase that I just added. It can.

Since this test is working, it implies to me that I am looking at the right device (/dev/sda4), and that each key slot on /dev/sda4 corresponds to a passphrase which is able to decrypt the disk. I understand that there are further "real keys" down the line, but what it looks like to me, is that the Kubuntu installer sets up two passphrases able to open the system: one which I supplied during installation, and another mystery passphrase which I'm wondering what is.

I think this is a question of what the installer does with cryptsetup, rather than how cryptsetup itself works. I would like to understand if the second initial key really is another passphrase that can decrypt my system. Of course I could try to delete both the keys after setting up a new one, and that would leave me with just one. However, I am concerned that I am then stepping on the installer's toes somehow, causing problems. I am also just wondering out of interest why there are two initial keys.

---

### Post by alexmurray on 2022-03-20
The second key you asked about in the original post is the randomly generated recovery key - this was originally introduced in 21.04 - [https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221](https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221) - and then improved in 21.10 to allow it to be specified by the user and to make sure the randomly generated one is stronger - see [https://discourse.ubuntu.com/t/impish-indri-release-notes/21951](https://discourse.ubuntu.com/t/impish-indri-release-notes/21951)

---

### Post by efjen on 2022-03-21
Ah thanks, that explains it! I struggled with googling it until now; I didn't think to use the word recovery. I don't think the installer offered me any information or a choice in this, but I am happy now that I understand what it is.

---

