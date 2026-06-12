---
title: "apt-get"
date: 2010-03-08
forum: Server Platforms
---

### Post by edpatterson on 2010-03-08
Ubuntu Server 8.04

I have 2 servers in the same rack, on the same subnet, using the same DNS servers and build with the same media. On one of them the following command fails
```

apt-get install squid

```
On the other on the package was installed with out any problems. I have checked the /etc/apt/sources.list files and they are identical.

Actually, it could not find  mutt either.

Where do I go from here?

Ed

---

### Post by MelDJ on 2010-03-08
i think you had root priveleges on the other
try ```
sudo apt-get install squid
```

---

### Post by edpatterson on 2010-03-08
> **MelDJ said:**
> i think you had root priveleges on the other
try ```
sudo apt-get install squid
```

As bad as it is, I was logged in as root.
The actual error message reads "Couldn't find package squid"

---

### Post by MelDJ on 2010-03-08
did you just add the repo?
if yes, do 
```
sudo apt-get update 
```

followed by 
```
sudo apt-get install squid
```

---

### Post by edpatterson on 2010-03-08
> **MelDJ said:**
> did you just add the repo?
if yes, do 
```
sudo apt-get update 
```

followed by 
```
sudo apt-get install squid
```

That got it. I assumed the update only updated installed packages. I guess I have some more reading to do.

Thanks a million!

Ed

---

### Post by MelDJ on 2010-03-08
after adding a new repo, you must do an apt-get update to refresh your sources.
thats why squid didn't appear before you did the update

---

