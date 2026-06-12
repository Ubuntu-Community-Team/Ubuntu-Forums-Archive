---
title: "Encfs --reverse with existing config file"
date: 2016-02-19
forum: Security
---

### Post by Terror_Factor on 2016-02-19
Hi,

Is it somehow possible to use encfs --reverse with an existing config file (created by using encfs in normal mode)?
I'm using cloud storage, so I encrypted my files using encfs normally.
Now I have a big external drive that I also want to upload, and it seems a bit redundant to first move those unencrypted files to my normal encfs-setup, to get them uploaded (also, I don't have the space to move/copy everything to my internal drive).
So I wanted to use the reverse option and then upload the encrypted content to my online storage, but I get "The configuration loaded is not compatible with --reverse".

I tried changing a few parameters (namely set uniqueIV and chainedNameIV to 0, as that seems to be the main difference when creating a reverse config file), but of course that didn't work. 

I hope there's a better option than getting a second external drive to encrypt everything using the regular encfs setup, and then upload it?

It's a bit counterintuitive that you can only use the config file of the --reverse method in the other direction, and not the normal config, isn't it?

---

