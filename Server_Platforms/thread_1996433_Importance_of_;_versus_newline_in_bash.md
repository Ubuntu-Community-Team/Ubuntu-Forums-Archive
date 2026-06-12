---
title: "Importance of ; versus newline in bash"
date: 2012-06-04
forum: Server Platforms
---

### Post by umuro on 2012-06-04
Execute 
```

 bash -c "export var1=test 
 echo $var1"

```"

Or Execute
```
bash -c "export var1=test; echo $var1"
```and you'll see nothing.

You have to execute
```
bash -c "export var1=test; echo \$var1"
``` and you'll see test.

Don't forget to escape $!!!

Now you can build a script line on the fly and execute it.

---

