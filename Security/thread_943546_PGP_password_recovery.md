---
title: "PGP password recovery"
date: 2008-10-10
forum: Security
---

### Post by Sarmacid on 2008-10-10
Hello fellow ubuntu users.

A couple of nights ago, I got a pgp encrypted file and while trying to decrypt it I found out I forgot the passphrase x_x

Tried many I thought were the passphrases but no luck yet. Also tried a product that's made for [Windows]("http://downloads.zdnet.com/abstract.aspx?docid=239052"), but it won't bruteforce passphrases longer than 9 chars, and I'm sure my pass was at least 12 chars.

I've been also trying to bruteforce it with a script I came up with, but the problem is the dictionary I'm using(Wich I made up) isn't that great(Working on generating a couple more). The way I built the dictionary is taking some characters(I know the passphrase is built that way cause I got it from a song) and randomly combining them as shown in the attached excel sheet(Sorry that's what I got at work and google docs didn't get the formula right).

So I'm wondering if anyone has any advice as to how to do this.

Will post the script if anyone is interested in it, and maybe someone can point me to a program or script to make a decent dictionary.

Thanks in advance.

[COLOR="DarkRed"]***update***[/COLOR]

Managed to bruteforce my way in with a couple of scripts, 1 to generate the dictionary and 1 to try every word in the dictionary as a passphrase.

---

