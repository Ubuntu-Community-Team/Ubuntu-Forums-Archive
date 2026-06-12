---
title: "apache, php, execute programs : permissions?"
date: 2006-10-25
forum: Server Platforms
---

### Post by talz13 on 2006-10-25
I set up the x10 program to use with my old cp290 controller box, and got it working correctly.  Next, I'm working on making a web interface for it, and this is where I'm running into problems.

I know the apache process runs as a different user (web-httpd or something), and it appears that it doesn't have permissions to access /dev/x10 (the serial interface for the cp290 box).  I changed the apache process to my main user/group and the php page would work as expected, but that can't be a good solution.

Is there a way to let apache/php have access to the /dev/x10?  Or am I just going to have to work with my current user/groups?

Here's my code for the php page right now:
```
<html>
        <body>
<?php
$on     = '';
$off    = '';
if ($_GET["on"] > 0 && $_GET["on"] < 9)
{
        $on     = $_GET["on"];
        echo '<p>Turning on light ';
        echo  $on;
        echo '</p><br>';
        echo exec('x10 -n '.escapeshellarg($on));
}
if ($_GET["off"] > 0 && $_GET["off"] < 9 && strlen($on) == 0)
{
        $off    = $_GET["off"];
        echo '<p>Turning off light ';
        echo $off;
        echo '</p><br>';
        system('x10 -f '.escapeshellarg($off));
}
?>

                <p>Please select which light you want to turn on:</p>
                <FORM action="x10.php" method="GET">
                <INPUT type="radio" name="on" value="1">1
                <INPUT type="radio" name="on" value="2">2
                <INPUT type="radio" name="on" value="3">3
                <INPUT type="radio" name="on" value="4">4
                <INPUT type="radio" name="on" value="5">5
                <INPUT type="radio" name="on" value="6">6
                <INPUT type="radio" name="on" value="7">7
                <INPUT type="radio" name="on" value="8">8
                <INPUT type="submit" value="Turn it on!">
                </FORM>

                <p>Please select which light you want to turn off:</p>
                <FORM action="x10.php" method="GET">
                <INPUT type="radio" name="off" value="1">1
                <INPUT type="radio" name="off" value="2">2
                <INPUT type="radio" name="off" value="3">3
                <INPUT type="radio" name="off" value="4">4
                <INPUT type="radio" name="off" value="5">5
                <INPUT type="radio" name="off" value="6">6
                <INPUT type="radio" name="off" value="7">7
                <INPUT type="radio" name="off" value="8">8
                <INPUT type="submit" value="Turn it off!">
                </FORM>
        </body>
</html>

```

---

### Post by adwait on 2006-10-25
How about changing the ownership of /dev/x10 to www-data (that's what apache runs as I think...)

---

### Post by talz13 on 2006-10-25
I just tried that, but no go.  I've still only gotten it to work while running apache as a normal machine user account.

---

