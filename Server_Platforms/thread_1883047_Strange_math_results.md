---
title: "Strange math results"
date: 2011-11-18
forum: Server Platforms
---

### Post by osx on 2011-11-18
Ran into a strange problem that appears to be software related, but not sure how to confirm it. Was wondering if anybody could give me some ideas as to whether this is a bug or a configuration issue and how to go about either reporting it or correcting it on my end if it is a configuration issue.

While trying to write a decimal to base-32 converter, in PHP, I ran into a strange math result.

If I run this code:

```
<?php
$result = 657911351231 / 32;
echo $result;
?>
```

On an Ubuntu 8.04.4 LTS, 64-bit, server install the output is: 20559729726

On an Ubuntu 10.04.3 LTS, 64-bit, server install the output is: 20559729725.969

Why is the 8.04.4 system producing an inaccurate/rounded result?

Is this a configuration issue (PHP, OS, or otherwise) or a bug in PHP or something with Ubuntu itself?

The version of PHP on the 8.04.4 system is 5.2.4-2ubuntu5.18.
The version of PHP on the 10.04.3 system is 5.3.2-1ubuntu4.10.

I don't want to file a bug report if this is a configuration issue.

---

### Post by osx on 2011-11-18
I also get strange results doing this:

```

<?php

$result = 657911351231 / 32;

$result2 = floatval($result);
echo "floatval: ".$result2."\r\n"; // 20559729726

$result3 = intval($result);
echo "intval: ".$result3."\r\n"; // 20559729725

?>

```

Per the PHP manual, floatval() should return the float value of $result, but it is not in this example.

Also, $result3 is rounded down which indicates that a remainder is known, but I cannot get the remainder to show.

I can find no PHP bug reports on something like this which is leading me to believe something else is the cause. The system it is running on is a Dell server not even two years old so I don't think it is a CPU issue.

---

### Post by dtfinch on 2011-11-18
What if you try "657911351231.0 / 32.0"?

Though the documentation says integer division in php should give floating point results whenever the result is not a whole number, so 5.3.2 is giving the correct result. Either 5.2.4 is printing wrong or it's mistaking the result for an integer (it's [known](https://bugs.php.net/bug.php?id=39703) to return integers if it thinks it's appropriate).

If I were making a base32 converter from scratch, I'd try to use all integer bit arithmetic. ">>5" to divide by 32, and "&31" to get modulus 32.

Otherwise, php has a [base_convert](http://php.net/manual/en/function.base-convert.php) function that can handle bases up to 36.

---

### Post by Jonathan L on 2011-11-18
Hi Osx

> Ran into a strange problem that appears to be software related, but not sure how to confirm it. Was wondering if anybody could give me some ideas as to whether this is a bug or a configuration issue ...This appears to be a bug in earlier PHP, now fixed.  The arithmetic is correct, the printing is unexpected for numbers >= 10^11.

If you care about it, perhaps you can change the output with printf or appropriate rounding.  In my opinion, the later PHP is doing the correct thing, as echo 1 / 2 will show 0.5.

It looks like they did a clean up in 5.3.0: [http://www.php.net/ChangeLog-5.php](http://www.php.net/ChangeLog-5.php) says:
> Changed floating point behaviour to consistently use double precision on all   platforms and with all compilers. (Christian Seiler)
Changed round() to act more intuitively when rounding to a certain precision   and round very large and very small exponents correctly. (Christian Seiler)The bug is easily reproduced:
```

<?php
$x = 99999999999.1;
echo $x, " ", 100000000000 - $x, "\n";
++$x;
echo $x, " ", 100000000000 - $x, "\n";
--$x;
echo $x, " ", 100000000000 - $x, "\n";
?>

```On PHP 5.2.10 (on 32-bit Ubuntu 9.10 server):
```
99999999999.1 0.899993896484
100000000000 -0.100006103516
99999999999.1 0.899993896484
```On PHP 5.3.2 (on 32-bit Ubuntu 10.04 desktop):
```
99999999999.1 0.89999389648438
100000000000[COLOR=Red].1[/COLOR] -0.10000610351562
99999999999.1 0.89999389648438
```Kind regards,
Jonathan.

---

### Post by osx on 2011-11-18
> **dtfinch said:**
> What if you try "657911351231.0 / 32.0"?

Still the same problem.


> **dtfinch said:**
> Otherwise, php has a [base_convert](http://php.net/manual/en/function.base-convert.php) function that can handle bases up to 36.

Tried base_convert() but it produced erroneous results regardless of the version of Ubuntu I ran it on.

Thanks for the ideas, though.

---

### Post by osx on 2011-11-18
> **Jonathan L said:**
> 
This appears to be a bug in earlier PHP, now fixed.  The arithmetic is correct, the printing is unexpected for numbers >= 10^11.

If you care about it, perhaps you can change the output with printf or appropriate rounding.  In my opinion, the later PHP is doing the correct thing, as echo 1 / 2 will show 0.5.

It looks like they did a clean up in 5.3.0: [http://www.php.net/ChangeLog-5.php](http://www.php.net/ChangeLog-5.php)

Thanks for the info. That's a big relief. I hate it when I can't figure out the cause of the problem.

I posted it on Launchpad at [https://answers.launchpad.net/ubuntu/+question/179259](https://answers.launchpad.net/ubuntu/+question/179259). Maybe they'll update PHP for 8.04.4.

---

### Post by Jonathan L on 2011-11-18
Hi again Osx

> 
I posted it on Launchpad at [https://answers.launchpad.net/ubuntu/+question/179259](https://answers.launchpad.net/ubuntu/+question/179259). Maybe they'll update PHP for 8.04.4.

You might like to update your question there: definitively it's not the arithmetic, it's the conversion from float to string.  You get the same results with printf("%s", $x), but you get correct results with printf("%20.10f", $x).  Even though they print without decimal point, the results are definitely floats of the correct value.

Kind regards,
Jonathan.

---

