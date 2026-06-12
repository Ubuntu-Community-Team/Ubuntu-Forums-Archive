---
title: "Error message in both terminal and software updater???"
date: 2012-08-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by chrissy.millichamp on 2012-08-20
This suddenly appear in software updater and and updating in the terminal. Plz need help!!!
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages:](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages:) 404  Not Found [IP: 199.47.217.170 80]
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages:](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages:) 404  Not Found [IP: 199.47.217.170 80]
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_binary-amd64_Packages: Hash Sum mismatch
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_binary-i386_Packages: Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Couldn't rebuild package cache

---

### Post by cariboo on 2012-08-21
> **chrissy.millichamp said:**
> This suddenly appear in software updater and and updating in the terminal. Plz need help!!!
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages:](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages:) 404  Not Found [IP: 199.47.217.170 80]
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages:](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages:) 404  Not Found [IP: 199.47.217.170 80]
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_binary-amd64_Packages: Hash Sum mismatch
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ca.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_binary-i386_Packages: Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Couldn't rebuild package cache

Do you get these errors every time you try to do an update? The first error is pretty self-evident, all you have to do is get the public key for the spotify repository and add it to the Authentication section of software-sources-gtk. 

I'm not sure about the dropbox error, but it could probably just be a temporary problem.

I'd suggest switching to the main repository server to repair the last error.

---

### Post by chrissy.millichamp on 2012-08-21
How do I add or switch the repositories in software sources, and if so I dont see them?

---

### Post by ventrical on 2012-08-21
> **chrissy.millichamp said:**
> How do I add or switch the repositories in software sources, and if so I dont see them?


Click settings/repositories

then click the little dialog box that says "Download From:"

---

### Post by chrissy.millichamp on 2012-08-21
I may sound like an idiot, but of course not. So now, what do I do from there?

---

### Post by ventrical on 2012-08-21
> **chrissy.millichamp said:**
> I may sound like an idiot, but of course not. So now, what do I do from there?

If your current server is from the US then try Main. If it is Main, try the US (United States)

Also you can make sure you check your repositories that "Canonical Partners" is checked off also.

synaptic/settings/repositories/

---

### Post by chrissy.millichamp on 2012-08-21
But I cant seem to see the fallowing  repositories above that constantly gives me errors while updating, and I am Canadian Sever, so....

---

### Post by dino99 on 2012-08-22
use synaptic to deal with these ppas

---

