---
title: "Made some really stupid GPG mistakes"
date: 2008-08-05
forum: Security
---

### Post by Alpha_Cluster on 2008-08-05
Ok so about 2 years ago I made about 2 big mistakes in a row followed by something going wrong I think about a year later that I still don't understand.

Basically do to many stupid reasons I have 3 GPG public keys that will never expire and 1 correct key (read i still have the private key). The problems with this started when I originally learned about GPG keys and thus decided to create one for my private accounts (a less used email address) and one for more public accounts. In my infinite wisdom of the time I decided to create 2 keys that never expired. (somehow one of those keys does not even match between key servers but htat is a different story) 

The problem arised about a year ago when i was moving back to ubuntu after using Gentoo for awhile and I had a huge data loss incident involving partitions that shouldn't have gotten deleted being deleted. Needless to say i lost two private keys of which i could only find one revoktion certificate (though it seemed to not work on all servers from the looks of it). Then after that I made a new single key that was just for signing apps and for my Ubuntu LoCo team stuff. This one I lost somehow and somehow the revoktion key also was lost in the 2-3 moves I had since I created it.

Since then I know use a key the expires in case I ever loose it but I want to know if anyone has any way to make sure these old keys never get used somehow (as from what I have read they cannot get removed from the key servers)? 

So far my only idea has been to get some people and me to sign them as untrusted. What do people think about this idea?

---

### Post by Oldsoldier2003 on 2008-08-05
There really isn't much you can do about it. Just make sure that you let people know which key is the correct key to use when encrypting to you.

---

