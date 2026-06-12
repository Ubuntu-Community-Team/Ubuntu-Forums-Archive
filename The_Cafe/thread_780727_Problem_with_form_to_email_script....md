---
title: "Problem with form to email script..."
date: 2008-05-03
forum: The Cafe
---

### Post by Old Marcus on 2008-05-03
Not sure if this is the right place, but anyway.

I used a php script with an html form to make a user feedback form and theoretically it works. I do not get any errors. But tha supposed email does not turn up in my email inbox. Any idea for this?

Code:

```
<form method="post" action="sendmail.php">
  Your Email: <input name="email" type="text" /><br />
  Message:<br />
  <textarea name="message" rows="15" cols="40">
  </textarea><br />
  <input type="submit" />
</form>
```

```
<?php
	$email = $_REQUEST['email'] ;
	$message = $_REQUEST['message'] ;

if ( ereg( "[\r\n]", $name ) || ereg( "[\r\n]", $email ) ) {
header( "Location: http://majicalyouth.co.uk/error.php" );

}

	if (!isset($_REQUEST['email'])) {
	header( "Location: http://majicalyouth.co.uk/contact.php" );
	}
	elseif (empty($email) || empty($message)) {
    	header( "Expires: Mon, 3 Dec 2012 01:00:00 GMT" );
    	header( "Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT" );
    	header( "Cache-Control: no-cache, must-revalidate" );
    	header( "Pragma: no-cache" );
	header( "Location: http://majicalyouth.co.uk/error.php" );
	}
	else {

	mail( "marcus_orentius[at]yahoo.co.uk", "Email from potential volunteer",
	$message, "From: $name <$email>" );
	header( "Location: http://majicalyouth.co.uk/thankyou.php" );
	}
?>
```

I'm currently running this off my own computer with LAMP Server installed. Could it be because my computer is not properly configured as a server and the email isn't going out?

---

### Post by Old Marcus on 2008-05-04
Any help on this?

---

