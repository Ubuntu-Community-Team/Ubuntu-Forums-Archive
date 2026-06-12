---
title: "need help/info on verifying a sha256sums.gpg file"
date: 2015-03-06
forum: Security
---

### Post by sam_baker2 on 2015-03-06
hi,
I downloaded a file and I am trying to verify the integrity of the file using the sha256sum program.
I have both the SHA256SUMS file and the the SHA256SUMS.gpg file in the same folder.

when I do this:
```
gpg --verify SHA256SUMS.gpg SHA256SUMS   
``` 
I get this:
```

gpg: Signature made Thu 19 Feb 2015 04:28:12 PM CST using DSA key ID FBB75451
gpg: Can't check signature: public key not found  
```

Then, when I do this:
```
  sha256sum -c SHA256SUMS 2>&1 | grep OK     
```
I get this:
```
 OK         
```

Is the SHA256SUMS file good to use or do I need to get the public key?

Thanks

---

### Post by sam_baker2 on 2015-03-06
I finally solved this.
I had some settings in my firewall that were apparently conflicting with obtaining the key.
I turned the firewall off and I was able to get the key using:
```
 gpg --recv-keys FBB75451 
```

---

