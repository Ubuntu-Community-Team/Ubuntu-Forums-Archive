---
title: "Server script execute permissions"
date: 2010-09-16
forum: Server Platforms
---

### Post by wbu on 2010-09-16
I'm running Ubuntu 10.04 server with Apache 2, PHP5, MySQL, OpenVPN, IspCP, etc. How can I execute the pkitool script (for users to generate their own private keys and certificates without interaction) from openvpn via a web-interface? I have tried setting the GID, adding root-permission for www-data and vu2001 to that script in sudoers, etc. It always has a problem writing a log file and reading the server crt and key files, as the user is not root.

Is there ANY way to solve this problem? :( I will not make everything r+w to the world, though! Any help will be appreciated, as I'm stumped ...

---

### Post by BkkBonanza on 2010-09-17
You definitely shouldn't change file permissions to make this work. Pkitool is a wrapper for openssl so you may have better results using openssl directly. You should be able to use sudoers to enable this but how you set it up and execute the command makes a big difference to whether it will work. Even if you give permission to use openssl you will need to run the command using sudo still so that it runs as root. Otherwise it won't have access to the CA key file. 

I'm not sure offhand how that command must be spawned in PHP. You may be able to prefix "sudo" to the command string, or you may have to use a function parm to indicate uid=0 to run as root. When you attempt this you can check the PHP error log for any problems with spawning the process.

-----
As an aside, I wanted to mention that this methodology is actually the incorrect way to go about it. It's probably the way many web apps do it, but is insecure for the end user and when you go to buy a client/server certificate from a CA they don't do it this way.

The correct way is to generate the private key at the user end (in browser) so that it remains private. In the method above you are generating it on the server and the user has to trust that you delete the private key after giving it to them. They trust that you won't impersonate them or "lose" the private key to hackers or other users. What should happen is the browser is used to generate the private key, store it on the users system (certificate store in browser) and send the CSR (signing request) to the server. The server signs it with it's key, and returns the valid CRT (certificate) to the user (again stored in browser).

The problem is that each browser has different ways for doing the key gen and csr. So it becomes a hassle do it the correct way. For example, IE uses the [CertEnroll COM]("http://blogs.msdn.com/b/alejacma/archive/2009/01/28/how-to-create-a-certificate-request-with-certenroll-javascript.aspx?PageIndex=2#comments") object and Mozilla uses an [XPI object]("https://developer.mozilla.org/en/JavaScript_crypto"). Doing this process in the browser seems to be practically a "black art" since there is very little info around the web on it. But the "real" CAs use this method when issuing a certificate.

However, this doesn't solve your initial problem because even if you do it correctly you still need to execute openssl on the server to sign the user's CSR and return the CRT. I only mention because you may not know that generating the private key for users on the server is incorrect (though easier). Most end users won't realize the security problem but it does exist.

---

### Post by BkkBonanza on 2010-09-17
I did a little testing here because I was interested in how this works. Here is an example PHP script that does certificate requests for Firefox, Safari, Opera. Not Windows as that would require changing the html to use ActiveX. This does work on my test server here and when you submit the page a certificate is created and sent back to Firefox, and stored in it's certificate store.

```
<?php  // script to test client certificate creation

$cacfg="/var/local/ca/openssl.cnf";
$pwd="put-pwd-here";
$tmppath="/tmp";

if(!isset($_POST['cert_request'])) {
?>
<!DOCTYPE html>
<h2>Request a cert</h2>
<form method="post" action="">
<p>Name: <input type="text" name="name" value="">
<p><keygen name="cert_request" challenge="la-dee-da" KEYTYPE="RSA">
<p><input type="submit" name="createcert" value="Generate">
</form>
<? }
else {
    $csr = tempnam($tmppath, "csr-");
    file_put_contents($csr, "SPKAC=".str_replace(str_split(" \t\n\r\0\x0B"), '', $_POST['cert_request'])."\nCN=".$_POST['name']);
    exec("sudo /usr/bin/openssl ca -config $cacfg -batch -spkac $csr -passin pass:$pwd", $data);
    unlink($csr);
    header("Content-Type: application/x-x509-user-cert");
    //print "<pre>";
    print join("\n", $data);
    // print "</pre>";
}
?>
```

The following line must be added to sudoers using visudo,

www     ALL=NOPASSWD: /usr/bin/openssl

(assuming your PHP runs as www, chg if different)

The CA data (cnf/index/serial/certs) is owned by root, but you could use an alternate user to limit possible abuse. Then the sudoers line would then specify which user www was allowed to run as, instead of root. The CA directory must be outside the web path. I chose /var/local/ca. I just happened to create my CA with TinyCA but other ways work too.

---

### Post by wbu on 2010-09-17
Thanks a million BkkBonanza! I tried running openssl directly from php, but did not have the user-permissions in the sudoers list. That was probably one of my problems.

I know how it is supposed to work (the correct way) to generate the certificates, and I also know about the security risks. I just don't like the correct way, and my application on the users PC will also not do it the correct way! For that reason I have changed my implementation strategy.

I have written a PHP script that is started at boot and runs as a daemon in the background as root. Requests for new certificates, renewals, revocations and signing are just written to a specific file which the bg PHP-script then handles. This way I can make the server more secure as I can again disable the exec PHP command. It also gets around the permissions problem. :D

Thanks for the help in any case. I've found a lot of help here just as a guest by searching the forum, but this time I could not find what I was looking for, therefore the post. Great community! ):P

---

