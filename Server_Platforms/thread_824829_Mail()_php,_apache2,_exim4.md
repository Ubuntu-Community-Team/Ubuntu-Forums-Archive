---
title: "Mail() php, apache2, exim4"
date: 2008-06-10
forum: Server Platforms
---

### Post by deth4uall on 2008-06-10
I have a problem with my mail program. I am using exim4, and it runs smoothly from my phpBB3 program which is not set for a SMTP setting on another server. It has it set as mail(), and I am using this code for a retrieval system for my game:
```

	  $headers  = 'MIME-Version: 1.0' . "\r\n";
	  $headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";
	  $headers .= 'From: admin@ultimate-battle-online.com' . "\r\n";
	  $headers .= 'Reply-To: admin@ultimate-battle-online.com'."\r\n";
		$headers .= 'Sender: <admin@ultimate-battle-online.com>'."\r\n";
		$headers .= 'Date: ' . date('r', time())."\r\n";
		$headers .= 'X-Priority: High'."\r\n";
		$headers .= 'X-MSMail-Priority: High'."\r\n";
		$headers .= 'X-Mailer: PHP/' . phpversion()."\r\n"; 

  	$message = 'To: '.$user.'<br />From: UBO Admin<br /><br />Your account information was requested by '.$_SERVER["REMOTE_ADDR"].'<br />' . "\r\n";
	  $message .= 'Please click <a href="http://www.ultimate-battle-online.com/resetpass.ubo">Here</a> to reset your password.<br /><br />' . "\r\n";
	  $message .= 'Reset Code: '.$randpass.'<br />';
    
    ob_start();
  	mail($email, "Elemental Fury - Forgot Password", $message, $headers);
  	$err_msg = ob_get_clean();
  	$sent = 1 ;

```
The ob_start() always comes up clean... :S Any ideas?

---

### Post by deth4uall on 2008-06-10
I tried using some features from phpBB3 to add to headers but still its not going through... Any ideas?

---

