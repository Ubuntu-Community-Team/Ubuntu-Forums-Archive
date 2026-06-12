---
title: "File encryption question"
date: 2011-04-27
forum: The Cafe
---

### Post by hambone79 on 2011-04-27
Does anyone out there know of a open source tool that will allow me implement something basic digital rights management? I need to send confidential machine drawings to a vendor, but in the past the drawings have been leaked by careless e-mailing. Basically, I want to make it easy for them to access the files but I would like to make it difficult to e-mail it so many times it gets leaked accidentally.

I believe what I need is some sort of encryption where I can give the recipient a key that will tie it to their machine, or some way to limit the number of times they can forward it by e-mail.

I'm open to any suggestions, but above all I don't want to make it an annoyance for the vendor receiving the drawings.

---

### Post by jerenept on 2011-04-27
> **hambone79 said:**
> Does anyone out there know of a open source tool that will allow me implement something basic digital rights management? I need to send confidential machine drawings to a vendor, but in the past the drawings have been leaked by careless e-mailing. Basically, I want to make it easy for them to access the files but I would like to make it difficult to e-mail it so many times it gets leaked accidentally.

I believe what I need is some sort of encryption where I can give the recipient a key that will tie it to their machine, or some way to limit the number of times they can forward it by e-mail.

I'm open to any suggestions, but above all I don't want to make it an annoyance for the vendor receiving the drawings.

GPG encryption should work, but it would be a bit of an inconvenience to the vendor.

---

### Post by WRDN on 2011-04-27
If you're looking for strong file encryption, many applications support the three variants of AES (Advanced Encryption Standard) encryption - 128bit, 192bit and strongest of all, 256 bit. Examples of applications with support include 7-Zip.

The algorithm is widely used, and is employed to encrypt up to "Top Secret" level US Government documents.

---

### Post by NMFTM on 2011-04-28
> **jerenept said:**
> GPG encryption should work, but it would be a bit of an inconvenience to the vendor.
Once it's decrypted though, that wouldn't stop the recepient from sending the decrypted version to anyone they wanted to. Or if the public key was compromised, anyone from decrypting the file just as the recipient was able to.

---

### Post by hambone79 on 2011-04-28
> **NMFTM said:**
> Once it's decrypted though, that wouldn't stop the recepient from sending the decrypted version to anyone they wanted to. Or if the public key was compromised, anyone from decrypting the file just as the recipient was able to.

This is exactly what I'm afraid of, but I'm not sure how to prevent it. It seems like the only way is to setup some kind of server that will manage access.

---

### Post by Paqman on 2011-04-28
A technological solution is bound to be complex. 
If the documents are really sensitive you might want to get legal advice. Some kind of non-disclosure agreement and serialising the documents so you could trace them to their source if they were leaked maybe?

Either that or simply don't let them make their own copy of them.

---

### Post by hambone79 on 2011-04-28
> **Paqman said:**
> A technological solution is bound to be complex. 
If the documents are really sensitive you might want to get legal advice. Some kind of non-disclosure agreement and serialising the documents so you could trace them to their source if they were leaked maybe?

Either that or simply don't let them make their own copy of them.

Unfortunately it's pretty common for vendors to be careless with drawings even when there is a NDA in place. They can get away with it because of the disclaimer they put in their e-mail signature...it basically says if you are not the intended recipient you should delete the e-mail immediately.

---

### Post by Paqman on 2011-04-28
> **hambone79 said:**
> Unfortunately it's pretty common for vendors to be careless with drawings even when there is a NDA in place. They can get away with it because of the disclaimer they put in their e-mail signature...it basically says if you are not the intended recipient you should delete the e-mail immediately.

IANAL, but i'm pretty sure there's not many legal obligations you can actually wriggle out of with a disclaimer. Otherwise you could just use a disclaimer to get away with anything you wanted.

---

### Post by Thewhistlingwind on 2011-04-29
> **Paqman said:**
> IANAL, but i'm pretty sure there's not many legal obligations you can actually wriggle out of with a disclaimer. Otherwise you could just use a disclaimer to get away with anything you wanted.

AFAIK It's about as flimsy as a plastic ruler when it comes to legal protection. Though I don't think the OP wants a long (Costly) suit on their hands.

Unfortunately, there is no way to stop people from leaking information, besides only having trustworthy people look at it. Encryption can only go so far. Once the recipient has it, and has a decrypted copy, they can do whatever they want. 

Sorry.

EDIT: Just for clarification. IANAL (I Am Not A Lawyer) as well.

---

### Post by PhillyPhil on 2011-04-29
Give them access to your website where you allow them to view the drawings but not otherwise access them (bar the vendor manually taking screenshots of the website).

---

