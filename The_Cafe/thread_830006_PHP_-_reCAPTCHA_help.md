---
title: "PHP - reCAPTCHA help"
date: 2008-06-15
forum: The Cafe
---

### Post by Tux.Ice on 2008-06-15
please read below

---

### Post by Tux.Ice on 2008-06-15
anyone.

---

### Post by Tux.Ice on 2008-06-15
i really need some help w/ this.

---

### Post by Tux.Ice on 2008-06-15
nobody?

---

### Post by LaRoza on 2008-06-15
Pleade don't bump so often. Once every 24 hours is enough.

Also you might want to remove the personal information from the code in the meantime.

---

### Post by Tux.Ice on 2008-06-15
laroza - actually a second after i posted that laast bump i figured it out. closing the thread & removing personal info

---

### Post by magnus0 on 2008-06-15
You really can't use recaptcha with your site. The email form, it's action (what it's going to do after being pressed the submit button) is a mailto link. Recapthca can be used, if the action is a php file, that processes the info. You can use mail() in that file. You should use form2mail ([http://www.web4future.com/easiest-form2mail.htm](http://www.web4future.com/easiest-form2mail.htm)), then you can use captcha

---

### Post by Tux.Ice on 2008-06-15
read below

---

### Post by Tux.Ice on 2008-06-16
ok UPDATE:
i am trying to set it so that when recaptcha is valid it sets $recaptcha to "1" but if it is invalid sets it to "0". heres my recaptcha code:

```
<?php

require_once('recaptchalib.php');

// Get a key from http://recaptcha.net/api/getkey
$publickey = "6LdLMgIAAAAAADm2aLW7b8c6wo1OGRdyaGxg1xGN ";
$privatekey = "6LdLMgIAAAAAALEw_CSkv4BLdYCLUgpnkLLrkAnP ";

# the response from reCAPTCHA
$resp = null;
# the error code from reCAPTCHA, if any
$error = null;

# was there a reCAPTCHA response?
if ($_POST["recaptcha_response_field"]) {
        $resp = recaptcha_check_answer ($privatekey,
                                        $_SERVER["REMOTE_ADDR"],
                                        $_POST["recaptcha_challenge_field"],
                                        $_POST["recaptcha_response_field"]);

        if ($resp->is_valid) {
                echo "You got it!";
        } else {
                # set the error code so that we can display it
                $error = $resp->error;
        }
}
echo recaptcha_get_html($publickey, $error);
?>
```

the form which submits this information along with the username & password, etc is called submit.php and it is this ```
<?php


# You can pass following parameters in calling URL. They will
# override those specified below.
# user - new email user
# pass - password
# domain - email domain
# quota - email quota, Mb
# Example: cpemail.php?user=newuser&pass=password&quota=50



$cpuser = 'techo'; // cPanel username
$cppass = 'trustkn0w1.'; // cPanel password
$cpdomain = 'techotech.com'; // cPanel domain or IP
$cpskin = 'x';  // cPanel skin. Mostly x or x2. 


// Default email info for new email accounts
// These will only be used if not passed via URL
$edomain = 'techotech.com'; // email domain (usually same as cPanel domain above)
$equota = 512; // amount of space in megabytes



function getVar($name, $def = '') {
  if (isset($_REQUEST[$name]))
    return $_REQUEST[$name];
  else 
    return $def;
}

// check if overrides passed
$euser = getVar('user', '');
$epass = getVar('pass', $epass);
$edomain = getVar('domain', $edomain);
$equota = getVar('quota', $equota);
$recaptcha = getVar('recaptcha', $recaptcha);

$msg = '';
if ($recaptcha == "0")
while(true) {

  

  // Create email account
  $f = fopen ("http://$cpuser:$cppass@$cpdomain:2082/frontend/$cpskin/mail/doaddpop.html?email=$euser&domain=$edomain&password=$epass&quota=$equota", "r");
  if (!$f) {
    $msg = 'Cannot create email account. Error Code: 0xPHPSAFE98';
    break;
  }

  $msg = "<h2>Email account {$euser}@{$edomain} successfully created.</h2>";

  // Check result
  while (!feof ($f)) {
    $line = fgets ($f, 1024);
    if (ereg ("already exists", $line, $out)) {
      $msg = "<h2>Email account {$euser}@{$edomain} already exists.</h2>";
      break;
    }
  }
  @fclose($f);

  break;

}

?>

<?php echo '<div style="color:blue">'.$msg.'</div>'; ?>
```

---

