---
title: "Install and configure denyhosts on Ubuntu 10.04 server"
date: 2010-05-03
forum: Server Platforms
---

### Post by osx on 2010-05-03
I've been running denyhosts on Ubuntu 8.04 servers without any problems using the how-to found here [http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts")

Now that I have a new Ubuntu 10.04 server running, I thought I would just install denyhosts from the Ubuntu repository not realizing that the paths and filenames of the install are different from the how-to I am used to using.

I figured out what the name of the new denyhosts config file is (at least new to me) and the new location, but I'm not sure about the "allowed-hosts" config file.

Does anybody know where the new path for this file is and whether the filename is still the same?

Thanks.

---

### Post by cariboo on 2010-05-04
If you run:

```
locate denyhosts
```

it will give the complete listing of where all the files are located.

---

### Post by osx on 2010-05-04
> **cariboo907 said:**
> If you run:

```
locate denyhosts
```

it will give the complete listing of where all the files are located.

Thanks, cariboo907. I guess I just missed the detail in the /etc/denyhosts.conf file I was looking for. Must have had tired eyes.

I used to put the "allowed-hosts" file in /usr/share/denyhost/data/, but the "data" directory doesn't exist in 10.04. Once I found the working directory information in the denyhosts.conf file and another reference to the allowed-hosts file, I got it all figured out.

Appreciate the response.

---

