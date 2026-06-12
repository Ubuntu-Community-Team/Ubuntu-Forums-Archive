---
title: "useradd -p and php crypt"
date: 2007-06-20
forum: Server Platforms
---

### Post by itsalmostreal on 2007-06-20
im looking to use php to generate a password that is already encrypted for the useradd command. can i use crypt for this? do i need to obtain the salt somewhere?

heres what i have...

$name = $user_info['full_name'];
$username = strtolower(str_replace(" ", "_", $name));
$password = substr(md5($username), 0, 8 ));
$enc_password = crypt($password, "???");

	$exec = "sudo useradd -m -c \"".$name."\" -p ".$enc_password." ".$username;
	$shell = exec($exec);

print 'username: '.$username."<br>";
print 'password: '.$password."<br>";

thanks!

---

