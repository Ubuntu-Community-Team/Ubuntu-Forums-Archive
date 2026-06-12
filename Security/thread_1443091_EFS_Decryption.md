---
title: "EFS Decryption?"
date: 2010-03-30
forum: Security
---

### Post by kleskjr on 2010-03-30
Hi guys,

my girlfriend got an interesting problem. She has encrypted her external HDD (photo folders) in vista a couple of months ago and then reinstalled a fresh windoze 7 on the vista. Do you think that it is possible to decrypt the files without any key?
hope that there is some solution..
cheers

---

### Post by jimv on 2010-03-30
That data is as good as gone if she reinstalled Windows.  The decryption keys are associated with her Windows account, and if they are deleted (which they were in this case), there is NO way to get them back and thus no way to decrypt the drive.  There are companies that advertise that they can, but they are lying and will just take your money.

---

### Post by kleskjr on 2010-03-30
apparently I have copies of lots of the photos she can not recover, so it means that theoretically we can find the keys for them. But I don't know if every single file has its own identical key, uncorrelated with the other ones..
maybe I can do my master thesis on this ;)

---

### Post by jimv on 2010-03-31
Well, the keys aren't tied to the files.  It's just one key per Windows user.  There's a key file that could have been backed up before reinstalling Windows, but now that file is gone :(

---

### Post by HermanAB on 2010-03-31
As far as I know, Windows Bitlocker is secure.  So your friend is now the proud owner of a large number of random bits...

---

### Post by kleskjr on 2010-03-31
> **HermanAB said:**
> As far as I know, Windows Bitlocker is secure.  So your friend is now the proud owner of a large number of random bits...

I don't think that they will be random. The only way to be random is when the key is the same size as the file, which I doubt. The key being much smaller then the file will preserve much of the underlying data correlations. So knowing something a priori about the file and what it contains it is possible to find the key(or at least some parts of it). Of course this is theoretically :)

just found some information in the net that by default the key length is 2Kb..which could need serious computational power.. so people please be careful when you encrypt your data ;)

---

