---
title: "Php"
date: 2009-03-25
forum: Server Platforms
---

### Post by quikone8 on 2009-03-25
Would someone look at this PHP code snippet, I am pretty sure I am doing something incorrectly.  I am trying to get information from a user field into this invoice template.  Or is there a debug program that works well with Ubuntu?

---

### Post by MaWaLe on 2009-03-25
Sorry for asking : but where is the code snippet ????

---

### Post by quikone8 on 2009-03-25
That would help wouldn't it, sorry.  Thanks for the quick reply.

Ron

<?php
echo t('Pickup Location:');
?>
<?php
            global $user;
            $profile = profile_load_profile ($user);
            echo $user->profile_pickup;
         
?>
<?php
}
?>

---

### Post by ianhaycox on 2009-03-25
Maybe
```

echo $profile->profile_pickup;

```

---

### Post by MaWaLe on 2009-03-25
two points :
1-
[PHP]<?php
echo t('Pickup Location:');
?>[/PHP]

the T is for what?

2-
[PHP]<?php
}
?>[/PHP]
this closing bracket is intended to close waht?

---

### Post by quikone8 on 2009-03-25
> **MaWaLe said:**
> two points :
1-
[PHP]<?php
echo t('Pickup Location:');
?>[/PHP]

the T is for what?

2-
[PHP]<?php
}
?>[/PHP]
this closing bracket is intended to close waht?

1- Just showing in text what the field is for.
2- I think the t is a typo, I thought I needed the closing bracket.  Just getting started with this so thanks for the critique.  Is there a good program that I could use with a browser or terminal to debug?  

BTW how is the testing going with Jaunty?

Ron

---

### Post by quikone8 on 2009-03-25
> **quikone8 said:**
> 1- Just showing in text what the field is for.
2- I think the t is a typo, I thought I needed the closing bracket.  Just getting started with this so thanks for the critique.  Is there a good program that I could use with a browser or terminal to debug?  

BTW how is the testing going with Jaunty?

Ron

I removed the stray t and the closing bracket and get this when it runs; Parse error: syntax error, unexpected $end in /var/www/modules/ubercart/uc_order/templates/customer.itpl.php on line 262.

Line 262 ends the script with </table>

---

