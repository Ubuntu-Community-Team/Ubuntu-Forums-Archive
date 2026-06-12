---
title: "ERROR: Setting a index [login,class] that isnt predefined (phpldapadmin 1.2.0)"
date: 2009-10-27
forum: Server Platforms
---

### Post by supremedalek on 2009-10-27
I decided to update phpldapadmin from the version 1.1.0.5 that is available as an ubuntu package to 1.2.0. Well, I seem to be having an issue with the [login,class] index:

```
$servers->setValue('login','class',array('posixAccount'));

```

The error I am getting looks like this

```

Function error called incorrectly [ERROR: Setting a index [login,class] that isnt predefined.]
```

Is this index now deprecated in 1.2.0? Anyone?

---

