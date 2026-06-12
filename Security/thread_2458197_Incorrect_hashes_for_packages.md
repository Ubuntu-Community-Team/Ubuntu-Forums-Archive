---
title: "Incorrect hashes for packages"
date: 2021-02-18
forum: Security
---

### Post by stripecat2 on 2021-02-18
Hi

Ran apt update a few minutes ago, and got this:

```
"Get:1 [http://se.archive.ubuntu.com/ubuntu focal-updates/main]("http://se.archive.ubuntu.com/ubuntu%20focal-updates/main") amd64 libssl-dev amd64 1.1.1f-1ubuntu2.2 [1&#8239;582 kB]
Err:1 [http://se.archive.ubuntu.com/ubuntu focal-updates/main]("http://se.archive.ubuntu.com/ubuntu%20focal-updates/main") amd64 libssl-dev amd64 1.1.1f-1ubuntu2.2
  Hash Sum mismatch
  Hashes of expected file:
   - SHA512:d70132eee70c570b6378e6e70e932ffe5562ea8f944e4dfcb11dd58383a880e4bc8973f64b60fcbf01ed82763ebe0d99a2d414ad8e63eae4bf011a96e6ad06a7
   - SHA256:880be109cdd2d78c2c477bdedf3dc07b9671fdb4b8b0935facce9a7a491821ef
   - SHA1:d60eed38534044e0f24efbc8c8614d42488086e0 [weak]
   - MD5Sum:9fd0bd013eccb06345954b740d9d4828 [weak]
   - Filesize:1581576 [weak]
  Hashes of received file:
   - SHA512:e514abdcb37e55bc9546e2377898a572a7dcf03ce1ca5d46661b42e7193bf5ab6234c25b9fda2e1aa137bd19e89c8785b8fe766e52f85c1898270588c68d97b8
   - SHA256:1aee50bbf522fe5d919d870549497368f249958df91091eb99e3753c6805a8c8
   - SHA1:a531be8ddc1f2b9d7a1f7f53eaa78d2c6ada3c2f [weak]
   - MD5Sum:bfe685677a6f9462460ce6cddd7389af [weak]
   - Filesize:1581576 [weak]
  Last modification reported: Thu, 18 Feb 2021 12:15:05 +0000
Fetched 1&#8239;582 kB in 0s (8&#8239;754 kB/s)
E: Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_1.1.1f-1ubuntu2.2_amd64.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_1.1.1f-1ubuntu2.2_amd64.deb)  Hash Sum mismatch
   Hashes of expected file:
    - SHA512:d70132eee70c570b6378e6e70e932ffe5562ea8f944e4dfcb11dd58383a880e4bc8973f64b60fcbf01ed82763ebe0d99a2d414ad8e63eae4bf011a96e6ad06a7
    - SHA256:880be109cdd2d78c2c477bdedf3dc07b9671fdb4b8b0935facce9a7a491821ef
    - SHA1:d60eed38534044e0f24efbc8c8614d42488086e0 [weak]
    - MD5Sum:9fd0bd013eccb06345954b740d9d4828 [weak]
    - Filesize:1581576 [weak]
   Hashes of received file:
    - SHA512:e514abdcb37e55bc9546e2377898a572a7dcf03ce1ca5d46661b42e7193bf5ab6234c25b9fda2e1aa137bd19e89c8785b8fe766e52f85c1898270588c68d97b8
    - SHA256:1aee50bbf522fe5d919d870549497368f249958df91091eb99e3753c6805a8c8
    - SHA1:a531be8ddc1f2b9d7a1f7f53eaa78d2c6ada3c2f [weak]
    - MD5Sum:bfe685677a6f9462460ce6cddd7389af [weak]
    - Filesize:1581576 [weak]
   Last modification reported: Thu, 18 Feb 2021 12:15:05 +0000"
```

When I ran apt update and tried again, no problems were reported. Is this any cause for concern or should I simply let it go?

Regards
Erik Zalitis

---

### Post by Bashing-om on 2021-02-18
stripecat2; Hello - Welcome to the forum.

Likely just that the mirror that you are accessing was in the process of syncing up with "mother". Now that the mirror is up-2-date all shows good:
see:
[http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error](http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error)
for a hashing of this type of situation.

[INDENT]these things happen
[/INDENT]

---

### Post by stripecat2 on 2021-02-25
... And here we go again...

```
50~20.04.1 [40,2 MB]
Fetched 193 MB in 16s (11,8 MB/s)
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python3.8/libpython3.8_3.8.5-1~20.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python3.8/libpython3.8_3.8.5-1~20.04.2_amd64.deb)  Hash Sum mismatch
   Hashes of expected file:
    - SHA512:ec571cb3933fe4e4e0149ae5f27dcea190681e472ad3dfb9e8e2a0d97ec41d1c3c93414b88e11f73c318edc36e04620ac1146eff5e129b49202c99f61a15a439
    - SHA256:197570dbeedf10f92a47b8c3b171acb23b444512d56cd0e75cfa7401766eddc1
    - SHA1:3b10f5743fef5df718b03afa9dc9fd99cdfbc7b8 [weak]
    - MD5Sum:11e464b0ae96f6e481a28f610126d0f8 [weak]
    - Filesize:1624136 [weak]
   Hashes of received file:
    - SHA512:74ff0c4fd3567b0cb8025457307d1f49823dac829055747dce7d74c05627d0e758a8008262103fbcbaf0c07eb32da0464c457a08cb6fc28bdbae5e163183aade
    - SHA256:ed49bfaaf66f207ec27b9ddc52018cde5e2c52d5d4336018570a9a8ae0a186a4
    - SHA1:c6f172747e992d370c88956d974e95530b98902b [weak]
    - MD5Sum:eefd04de050e60e0f3aed97ebb64dd1c [weak]
    - Filesize:1624136 [weak]
   Last modification reported: Thu, 25 Feb 2021 12:45:02 +0000
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I'm not sure this is nothing. I've been using Ubuntu since 2009 and this is not something you see to often... 

Thanks for the welcome message. I used to have an account here before. Nice to be back :)

---

### Post by DrScum on 2021-12-01
same problem with a brand new install 20.04.3 downloaded and installedtoday  (2021-12-1) what is wrong?? How do I fix this? I have tried so far the fixes available on the net 
[https://stackoverflow.com/questions/64120030/hash-sum-mismatch-when-apt-get-update-ubuntu-20-04-vm-with-multipass](https://stackoverflow.com/questions/64120030/hash-sum-mismatch-when-apt-get-update-ubuntu-20-04-vm-with-multipass)
but nothing helps.

---

