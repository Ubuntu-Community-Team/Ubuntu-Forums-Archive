---
title: "Path for git with user different of the apache"
date: 2016-08-25
forum: Server Platforms
---

### Post by sed_faster on 2016-08-25
Hello everyone,

I have a server apache with this structure folders and their permissions:
```

folderone: 700 apache:root sub_folder_git: 700 git:root

```

When I try do "git clone" on one respository on folder "sub_folder_git" I have problems because of level permissions. The solution I have was changed level permissions of the "folderone" to 777. But, which this folder management apache files I get worried.
When I changed the owner this folder, "folderone" the service apache, the website, is offline.

What do you suggest to resolve this situation?
Thanks

[UPDATE]
I was thinking about these structure permissions and I think haven't a good logic :P When I think the result is this :)

I need access on folder "sub_folder" and only user git should be access on this folder. But this folder is inside the folder "folderone". Once the user git when will write or read on folder "sub_folder" have to go through folder "folder_one", which have access only user apache.
This means which I will give access to the user git for the folder "folderone"?

---

### Post by sed_faster on 2016-08-26
Hello,

I am sorry to be upon this topic through comment my owner post but I haven't any idea about how I will resolve this problem. Thanks

---

