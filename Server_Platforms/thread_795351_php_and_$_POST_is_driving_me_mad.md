---
title: "php and $_POST is driving me mad"
date: 2008-05-15
forum: Server Platforms
---

### Post by theolster on 2008-05-15
OK this should be so simple I can't understand it.  I've got a fresh install of hardy, with Apache, MySQL & PHP installed.

But php seems not to be working properly.  I just want to post some thing from a form.  Here's the code:
```
<?php
    session_start();
    echo $_POST['login_email'];
?>

...

        <form action="/login" method="post" enctype="application/x-www-form-urlencoded">
	        <fieldset>
	            <label for="login_email">Email Address</label>
		    <input class="text" id="login_email" name="login_email" type="text" value=""/>
                    <label for="login_pass">Password</label>
                    <input class="text" id="login_pass" name="login_pass" type="password" maxlength="255" value=""/>
                    <input class="button" name="submit" type="submit" value="Login" />
            </fieldset>
        </form>
```
and I'm getting nothing, any help would be greatly appreciated.

---

### Post by hockey97 on 2008-05-15
well I havent' coded in php for a while so I will give you what I think might be the problem.


you first have to use a variable.

Try this  

<?php
    session_start();
$email = $_POST['login_email'];
    echo $email;
?>


also what is this?? <form action="/login"

is that a file? if so you need the extension.

like if it was a php file you would do /login.php.

Hope this helps.

---

### Post by theolster on 2008-05-15
Hi, you were semi-right about the action="/login" it should have read action="/login/", you don't need to expicitly name the file though.  If apache is set up to accept index.php as the default file in a folder (which it is by default) then the form will post to that file.

Also $_POST[...] is a variable, it's actually an array, so your example merely assigns one variable to another.  For future reference!

Thanks anyway, I'd been looking at it for over an hour and was convinced that the hardy release had screwed somthing up!

---

