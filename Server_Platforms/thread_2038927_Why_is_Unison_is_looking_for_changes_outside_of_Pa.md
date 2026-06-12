---
title: "Why is Unison is looking for changes outside of Path?"
date: 2012-08-07
forum: Server Platforms
---

### Post by Ralphie on 2012-08-07
When I start Unison, it searches for changes outside of my specified Path, but seems to only sync the actual Path folders, as it should. Why is it searching everything? And how can I go about stopping this? Some flag maybe? Maybe my preferences file incorrect?

```
# Unison preferences file on client

root =  ssh://server@XX.XXX.XXX.XX:XXXX//Path/To/BackupFolder

root = /Users/user

path = Documents/

path = Media/

perms = 0

servercmd=/usr/local/bin/unison

ignore = Name .DS_Store

ignore = Name *~

ignore = Name .*~

ignore = Name ._*

ignore = Name .localized
```

And then I'm running it with:

```
unison defaultbackup -repeat watch
```

It's checking everything within the user's home folder, instead of just the folders mentioned in Path (Documents / Media).

Any insight would be appreciated, thanks.

*Note I am using -repeat watch to continually monitor for changes in said folders.

---

