---
title: "John the Ripper Password Hashes?"
date: 2010-03-04
forum: Security
---

### Post by Onemajorflaw on 2010-03-04
I recently downloaded JTR to test my password for Windows 7. I used SAMdump2 and got my password hashes. I went back to JTR to read the hashes SAMDUMP2 found, and it loads four passwords, but then the line below that no password hashes loaded. Is there a step I'm missing? Or maybe another way to decipher the hash? I guess I shouldn't be too upset, I'm doing this to make sure my password is secure, and if I can't view it, that's a good thing right? Any help would be greatly appreciated.

---

### Post by HermanAB on 2010-03-04
Uhmm, WTF dude? Boot with Knoppix and reset the password to blank, reboot and set it to something again.

---

### Post by Onemajorflaw on 2010-03-04
> **HermanAB said:**
> Uhmm, WTF dude? Boot with Knoppix and reset the password to blank, reboot and set it to something again.

I don't want to reset the password. I know the password, I'm just testing it to see how secure it actually is...

---

### Post by cdenley on 2010-03-04
> **Onemajorflaw said:**
> I don't want to reset the password. I know the password, I'm just testing it to see how secure it actually is...

Did you use bkhive to remove the syskey encryption? Anyway, brute-forcing isn't what you have to worry about with NT hashes. Rainbow tables can crack hashes in a few minutes, typically. Just make sure your password isn't a dictionary word (or variation of a word), and use as many characters as possible with non-alphanumeric characters so it can't be cracked by the small rainbow tables. NT hashes aren't safe at all from physical access.

[http://ophcrack.sourceforge.net/tables.php](http://ophcrack.sourceforge.net/tables.php)

Cracking your NT hash isn't really the best (or fastest) way to determine the strength of your password.

---

### Post by Onemajorflaw on 2010-03-04
> **cdenley said:**
> Did you use bkhive to remove the syskey encryption? Anyway, brute-forcing isn't what you have to worry about with NT hashes. Rainbow tables can crack hashes in a few minutes, typically. Just make sure your password isn't a dictionary word (or variation of a word), and use as many characters as possible with non-alphanumeric characters so it can't be cracked by the small rainbow tables. NT hashes aren't safe at all from physical access.

[http://ophcrack.sourceforge.net/tables.php](http://ophcrack.sourceforge.net/tables.php)

Cracking your NT hash isn't really the best (or fastest) way to determine the strength of your password.

Yeah, I used bkhive on the "SYSTEM" file. I know it's not the best way to check for strength, but I am trying every avenue I can think of. Thanks for the tip.

---

### Post by boyi on 2011-06-12
Do you manage to crack your password after all?  When I tested windows 7 system, I use the following >  john --format:NT hashfile.  Dont forget to delete john.pot to re-crack the file. It did manage to crack simple password really fast though.   TQ.  Regards,  -Boyi-

---

