---
title: "bash: aliases vs functions"
date: 2019-10-16
forum: The Cafe
---

### Post by Skaperen on 2019-10-16
what is the general thought or opinion of bash users on making functions  in place of, or to serve as aliases?  for example, instead of:
```

alias term='kill -TERM'

```
doing:
```

term(){ kill -TERM "$@";}

```

i  find functions to be easier to code in more complex things, and also  easier to deal with when everything is in one place (e.g. doing  "set|less" to see them all).  thoughts?  opinions?

---

