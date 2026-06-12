---
title: "post variables doesnt work"
date: 2009-04-03
forum: Server Platforms
---

### Post by mentes on 2009-04-03
Hi,

I have installed ubuntu 8.10 with apache php mysql and it was working fine but couple of days ago php post variables didnt work and I dont know how to fix it could you please help me
Thanks

---

### Post by nquinnathome1 on 2009-04-03
What version of PHP do you have installed on your server? Have you changed anything recently on your server?

---

### Post by cdenley on 2009-04-03
Install this page somewhere on your server, browse to it, click the button, then post the text from the textarea box.
[PHP]
<html>
<body>
<form action="<?php print $_SERVER['PHP_SELF']; ?>" method="POST">
<input type="text" name="var1" value="value1"/><br/>
<input type="text" name="var2" value="value2"/><br/>
<input type="submit" value="Click Here"/><br/>
</form>
<textarea rows="6" cols="40">
<?php
print_r($_POST);
?>
</textarea>
</body>
</html>
[/PHP]

---

### Post by mentes on 2009-04-03
my php version is 5.2.4 and when I try to get any post variables it comes with empty I dont know why I didnt change anything recently on the sever

---

### Post by cdenley on 2009-04-03
Any examples, such as the one I posted?

---

### Post by mentes on 2009-04-03
I found php error log these lines maybe it can help it doesnt mean anything to me
[03-Apr-2009 17:04:57] PHP Warning:  Unknown: POST Content-Length of 23 bytes exceeds the limit of -201326592 bytes in Unknown on line 0
[03-Apr-2009 17:05:28] PHP Warning:  Unknown: POST Content-Length of 88 bytes exceeds the limit of -201326592 bytes in Unknown on line 0

---

### Post by cdenley on 2009-04-03
Post this output
```

grep post_max_size /etc/php5/apache2/php.ini

```

---

### Post by mentes on 2009-04-03
thank you very much I think it was because of post size it was 8000 I changed it and it works now

---

