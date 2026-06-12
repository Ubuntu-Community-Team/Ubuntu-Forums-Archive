---
title: "Is this a bug?"
date: 2010-05-01
forum: The Cafe
---

### Post by swoll1980 on 2010-05-01
In the .bashrc there is several if conditions that look like 
if [ -f /etc/bash_completion ]
If they are going to bother to check if the file exist, shouldn't they  make sure the file is readable? I'm new to this scripting, but it seemed kind of odd. Wouldn't -r be a better solution?

---

### Post by ibuclaw on 2010-05-01
Good point. But given the way that these files are packaged, they generally have the correct file permissions when you install them, so is never a worry.

You can't stop human interference / optimism though. But I can't imagine someone chmod -r /etc/bash.bashrc unless they knowingly intended to do that...

---

### Post by swoll1980 on 2010-05-01
> **ibuclaw said:**
> Good point. But given the way that these files are packaged, they generally have the correct file permissions when you install them, so is never a worry.

You can't stop human interference / optimism though. But I can't imagine someone chmod -r /etc/bash.bashrc unless they knowingly intended to do that...

So no then?

---

### Post by ibuclaw on 2010-05-01
> **swoll1980 said:**
> So no then?

You make perfect sense in your claim for using -r over -f. But I wouldn't regard it as a bug in in that respect. (May be worth wish-listing though).

---

### Post by swoll1980 on 2010-05-01
Ok. If it's not important I'll just pretend it never happened.  ;)

---

