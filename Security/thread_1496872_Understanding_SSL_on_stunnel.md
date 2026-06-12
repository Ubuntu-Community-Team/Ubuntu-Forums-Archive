---
title: "Understanding SSL on stunnel"
date: 2010-05-29
forum: Security
---

### Post by Trollbeater on 2010-05-29
Hello,

I recently setup stunnel to use to access an SSL enabled usenet account.  I was having difficulty for a few days and so I contacted the usenet provider.  stunnel is now working and I have tried both Pan and Knode without problems.  However, my usenet provider's response is confusing me.  They suggested that SSL can be accessed on any newsreader since it is a feature of my account.  But that can't be true of newsreaders that don't have an SSL enabled feature, can it?  I mean how would the information be decrypted?  

Can anyone provide some insight into how SSL works?  

Thanks,

---

### Post by johnkills on 2010-05-29
> **Trollbeater said:**
> Hello,

I recently setup stunnel to use to access an SSL enabled usenet account.  I was having difficulty for a few days and so I contacted the usenet provider.  stunnel is now working and I have tried both Pan and Knode without problems.  However, my usenet provider's response is confusing me.  They suggested that SSL can be accessed on any newsreader since it is a feature of my account.  But that can't be true of newsreaders that don't have an SSL enabled feature, can it?  I mean how would the information be decrypted?  

Can anyone provide some insight into how SSL works?  

Thanks,

My newbie guess is that SSL is only accessible to newsreaders that support SSL or using a software that would give another software with no SSL ability to use it. But I am guessing what your newsprovider means is that your "SSL account" can be used by any newsreader because if your normal newsreader dont have SSL it will automatically use the unencrypted version of usenet.

---

