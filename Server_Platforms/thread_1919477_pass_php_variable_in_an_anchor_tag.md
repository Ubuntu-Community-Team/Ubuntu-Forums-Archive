---
title: "pass php variable in an anchor tag"
date: 2012-02-02
forum: Server Platforms
---

### Post by subhojit on 2012-02-02
hello, i have written a code like this:

<a href="EditPage.php?id="<?php echo $UserId; ?>><input type="button" value="Edit account" /></a>

its cleat that i am trying to pass the php variable UserId using GET method, but its not working. am i doing any error or is there any other way to do this. help, please...

---

### Post by richardjh on 2012-02-03
Your php should be within the double quoted href. It should read as

```
<a href="EditPage.php?id=<?php echo $UserId; ?>" ><input type="button" value="Edit account" /></a>
```

---

### Post by subhojit on 2012-02-03
> **richardjh said:**
> Your php should be within the double quoted href. It should read as

```
<a href="EditPage.php?id=<?php echo $UserId; ?>" ><input type="button" value="Edit account" /></a>
```

thanks buddy

---

