---
title: "Problems with variables and Apache2"
date: 2005-10-01
forum: Server Platforms
---

### Post by niels on 2005-10-01
I can't send variables via php scripts.
I have set up a simple  test script like this:
```

<html>
<head>
<title></title>
</head>
<body>
<?php
print $test;
?>
</body>
</html>

```
Then I type this in my browser: localhost/~user/test.php?test=bla
But the script only returns a blank page... If I set the variable like in the script like this: $test = "bla"; there is no problems..
Then I tryed to pass the variable with af form and the get method in a script like this: 
```

<html>
<head>
<title></title>
</head>
<body>
<?php
if (isset($test)) {
print $test;
} else {
?>
<form action="test.php" method="post">
<input type="text" name="test">
<input type="submit" value="Send">
</form>
<?php } ?>
</body>
</html>

```
But it still returns a blank page...
How do I fix this problem?

---

### Post by DJ_Max on 2005-10-01
I cringe everytime I see someone trying to do what you're doing. Though I no longer use PHP.

First of all, this isn't a problem with Apache. This is a PHP configuration not allowing global variables. Which is a GOOD thing. There is no reason for you to use them, unless you want to get hacked. Read up on variable posioning and injection. Here's one from the site [http://www.php.net/manual/en/security.globals.php](http://www.php.net/manual/en/security.globals.php)
What you want is
```

<html>
<head>
<title></title>
</head>
<body>
<?php
print $_REQUEST['test'];
?>
</body>
</html>

```

---

### Post by giacomolg on 2006-03-18
Thank you DJ_Max.

---

