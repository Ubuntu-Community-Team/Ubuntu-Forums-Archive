---
title: "GPG/PGP. Is it hazardous to download the public key as well as the signature from the"
date: 2016-12-10
forum: Security
---

### Post by J_Me on 2016-12-10
I want to check a file but the developer has not listed their public key with a host (like sks-keyservers.net or mit) but instead has provided all the needed files on the same web page. From what I understand the whole point of using pgp/gpg is to safeguard against mitm attacks but doesn't downloading the public key and signature from the same web page go against the whole point of using gpg in the first place.
Confused

Edit: The title was too long, it should say
GPG/PGP. Is it hazardous to download the public key as well as the signature from the same web page.

---

### Post by Fire_Chief on 2016-12-12
Checking a file integrity is normally done with something like an MD5 hash checksum...not a GPG/PGP key (used for encryption). Doing a file check from a downloaded file where the hash is also listed is not dangerous. In fact, it is very important to ensure the file downloaded correctly and that you have an unaltered file (compared to what the developer released). So you download the target file, run an MD5 hash check on it and compare the hash output to the hash listed on the download page. They should match. If not, you should re-download the target file and repeat the process. Or notify the developer that the download may be corrupted/altered since you can't get the checksum to match. Note that some developers distribute hashes created with MD5 while others may do SHA-1 or some other hash type.

Cheers!

---

### Post by J_Me on 2016-12-13
@Fire_Chief
I believe I already understand what a GPG/PGP signature is used for(and that wasn't my original question) but I could be very wrong, so could you then please explain why Ubuntu provides a signature(.gpg file) alongside it's .iso for download. I don't mean to be rude when I say I don't need a best guess answer but the actual reason why.
For example from this link
[URL="https://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/16.10/release/"]https://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/16.10/release/
[/URL]To save your clicks here's a snippet from the link
```
[PARENTDIR] Parent Directory                                                                -   
[TXT] FOOTER.html                                                2016-10-13 15:51   27   
[   ] MD5SUMS                                                    2016-10-13 15:52  347   
[   ] MD5SUMS-metalink                                           2016-10-13 12:23  280   
[   ] MD5SUMS-metalink.gpg                                       2016-10-13 12:23  933   
[   ] MD5SUMS.gpg                                                2016-10-13 15:52  933   
[   ] SHA1SUMS                                                   2016-10-13 15:52  387   
[   ] SHA1SUMS.gpg                                               2016-10-13 15:52  933   
[   ] SHA256SUMS                                                 2016-10-13 15:52  507   
[   ] SHA256SUMS.gpg                                             2016-10-13 15:52  933   
[DIR] source/                                                    2016-10-13 11:29    -   
[   ] ubuntu-16.10-preinstalled-server-armhf+raspi2.img.xz       2016-10-13 15:22  245M  
[   ] ubuntu-16.10-preinstalled-server-armhf+raspi2.img.xz.zsync 2016-10-13 15:51  429K  
[   ] ubuntu-16.10-preinstalled-server-armhf+raspi2.manifest     2016-10-13 15:22   13K  
[   ] ubuntu-16.10-server-arm64.iso  


```As you can see from the snippet the .gpg signature has been provided
Thank you

---

### Post by Fire_Chief on 2016-12-13
Ah, yes. My misunderstanding there...sorry about that.
Per this article ([http://www.howtogeek.com/246332/how-to-verify-a-downloaded-linux-iso-file-wasnt-tampered-with/]("http://www.howtogeek.com/246332/how-to-verify-a-downloaded-linux-iso-file-wasnt-tampered-with/")), it's useful to note that the actual key that GPG uses to verify the signature *should* be hosted on a separate server and retrieved using GPG itself (not downloaded from a browser). So hosting the checksum and the signature of the checksum could indeed be manipulated to say the file is legitimate...except that the key used to verify all of this is not also in the download space or even on that same server. It is kept elsewhere. This would require a hacked/modified file to also use a hacked/modified key on a separate server to completely pass inspection. This is significantly harder to do.
The signature file that is provided is only that of the hash file as a way to verify that not only is the ISO file uncorrupted, but that the hash file itself is also uncorrupted. The validity of the signature, the hash file, and the download are all confirmed from the key file.

Hope this helps!

---

### Post by untrustytahr on 2016-12-13
```
From what I understand the whole point of using pgp/gpg is to safeguard against mitm attacks...

```
No, not really but it is one of its capabilities.

```
...doesn't downloading the public key and signature from the same web page go against the whole point of using gpg in the first place...

```

Presumably, you are worried that if a web server hosting the data file(s), signature file(s), and public-key were compromised then they could be replaced.  This is true, they could be... But if the server were compromised the data file(s) and signature file(s) could be replaced and the attacker could just as easily upload the public-key he/she used to a keyserver as well.  Keyservers don't reject 'bogus' keys.  I could create a key under the name "Edward Snowden" and upload it.  It doesn't make it the real key he would use.  That's why you pull up the fingerprint and verify the trustpath.

The important part for you is: what level of verification is acceptable to you to believe the public-key is genuine?  Meeting the individual in person?  Accepting the signature of someone you know who certifies they met the individual in person?  Accepting the posting of the public-key on the persons website?  Only you can determine what authentic is.

So I guess my point is: How you obtain the public key isn't important. How you verify it is.

---

### Post by DuckHook on 2016-12-13
@J_Me

Your question is a good one, but it actually contains a number of separate questions dealing with different issues. I will try to give you a very rough overview insofar as this layman understands it.

> **J_Me said:**
> &#8230;doesn't downloading the public key and signature from the same web page go against the whole point of using gpg in the first place&#8230;

The public key and the signature are two different animals intended to address two different problems.

[LIST=1]
[*]The public key is used to encrypt a file so that the contents can only be decrypted by someone with the private key.
[*]The signature is used to verify that any message (or file) that has been hashed with the private key *including those sent in the clear*:
[LIST=A]
[*]originated from the holder of the private key, and
[*][*]have not been altered or substituted.
[/LIST]
[/LIST]
Therefore, it is fine if they are displayed together on the same site.

> &#8230;the developer has not listed their public key with a host&#8230;

I don't quite understand what you mean by "host". Reading between the lines, it seems that your concern may have more to do with verification. Keys can be verified without residing on a host. They can also reside on a host without being verified.

[LIST=1]
[*]A verified key is one that has been signed by a trust authority (like VeriSign or a web of trust) such that the owner of the key is indeed who he says he is. Verification is not a trivial process and involves physical authentication procedures. The result is a reasonable level of assurance (trust) that a verified key belongs to the stated owner.
[*]A key hosted on a keyserver is nothing more than one that has been registered with a keyserver. In this case, the keyserver is not verifying the key, but merely taking a snapshot of it and storing it in a repository/database.
[/LIST]
Therefore, a hosted key does not mean that it has been verified. And a verified key does not have to be hosted.

> &#8230;the whole point of using pgp/gpg is to safeguard against mitm attacks&#8230;

pgp/gpg is designed to address numerous issues of which mitm attacks are only one, and a derivative one at that. Its main goals are actually: data privacy, data integrity and data authenticity. mitm attacks are only one of many attack methodologies that target these goals. Therefore, pgp/gpg safeguards against mitm attacks as a subset of safeguarding against *all* attacks in general.

Applying the above to the real world, the matter of trust is not simplistic and is largely one of context.

[LIST=1]
[*]An unsigned key between two parties who already know each other well is quite secure, so verification is superfluous. Examples: if you use your key with your spouse or your employer, a high level of trust already exists and, provided both parties keep their private keys secret, no higher authority is needed.
[*]On the other hand, if you are dealing with a stranger, especially one who is virtual and cannot provide physical evidence, the challenge of ascertaining identity is much greater. If all you care is that the file you are downloading from, say, launchpad is the same untampered file that was uploaded by the author, then again, verification is unncessary. In this case, launchpad has enforced that only keyholders can create accounts and any upload to a repository must be from the person who originally created it. This is done through keys. If the author is a rogue, this is not launchpad's problem. Its role is only to ensure that the author's file is genuine.
[*]If you wish to send sensitive data to an individual or agency who claims to be some sort of authority, then this is where verification comes in. Say, you are sending a copy of your passport to some embassy to obtain a visa. How do you know that the agency you are sending to is what it says it is? Signed keys offer some assurance.
[/LIST]
Verification, like most security issues, is layered. You can't have absolute assurance; only varying degrees, in which increasing security is almost always inversely proportional to decreasing convenience. Authors can be spoofed, by identity theft if nothing else.

EDIT: Ninja'd by untrustytahr.

---

### Post by cogset on 2016-12-13
> **J_Me said:**
>  (...)but doesn't downloading the public key and signature from the same web page go against the whole point of using gpg in the first place.
.

Besides what has been explained above, to somehow counteract this issue Tails for instance advises to download the key from different computers placed in different locations and check that they match (or even from the same computer at different times, if I recall correctly) - of course this is by no means bullet-proof, but I imagine it's still a bit better than get the key once and just trust it.

As far as I can understand, the issue of trust is the crucial point of public key encryption: I've read that even some experienced folks think this system in reality it's not  entirely reliable precisely because of this issue.

---

