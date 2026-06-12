---
title: "[Phone] Aquaris E4.5, vcf import doesn't work"
date: 2015-09-07
forum: Ubuntu Phone and Tablet
---

### Post by malibann on 2015-09-07
I tried an import of my contacs via multiple VCFs using syncevelotion.


```

cd /media/phablet/1234-1234
find ./ -name '*.vcf' -exec syncevolution --import {} backend=evolution-contacts \;

Note:
using '*.vcf' instead of *.vcf is important if you have VCFs with a whitespace the filename.

```


It seemed to work first because a lot of contact appeared on the contact list but none of them had a correct phone number, email address or anything useful except the name.

Isn't there any real working method for .vcf import? (Email doesn't work currently)

---

### Post by malibann on 2015-09-15
I have now successfully imported my contacts from my former phone.

- I had a list of .vcf files sent by bluetooth to an Android device (tablet)

- On my Android device I used a tool with the name "Import Contacts" from the Playstore.

- I exported the data on my Android device with the help of "McBackup" from the Playstore an sent it to my phone by EMail.

- I installed "Dekko" on my Ubuntu Phone, the last Mail I received had an attachment with the extension .VCF, when I upened it I coul easily import it into the contact list on my Ubuntu phone.

Thanks for all the help given in other threads before.

---

