---
title: "Problem Using apt-mirror"
date: 2013-05-23
forum: Server Platforms
---

### Post by chrisguk on 2013-05-23
I have apt-mirror running on my server.  It has downloaded the necessary files as per my distribution.

**The issue I am having is when I input the following command:**

```


sudo apt-get update
sudo apt-get install ruby1.8


```

**It gives me the following message:** :confused:

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ruby1.8
E: Couldn't find any package by regex 'ruby1.8'


```

I checked the folder in my browser and the file or package is present:

```


http://ubunturepo.simpson.home/ubuntu/pool/main/r/ruby1.8/


```

Does anyone have any expert experience with this?

---

### Post by chrisguk on 2013-05-25
*bump*

It surprises me that no one has answered this post yet. The matter is still not resolved and I have continued searching for a resolution.

---

### Post by newbie-user on 2013-05-30
did you add that repo to your /etc/apt/sources.list file?

---

