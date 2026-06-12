---
title: "Pure-ftpd and internet explorer"
date: 2007-04-18
forum: Server Platforms
---

### Post by abrown1983 on 2007-04-18
I do not know if it is possible to do, but I would like to have Internet Explorer prompt for a user name and password with a Pure-Ftpd server.  I have seen it done with Proftpd servers and have been told that enabling "BrokenClientsCompatibility=YES" on PureFtpd will fix it, however, after enabling, it still does not ask for a username or password.

I do understand that when using a browser, it defaults to a username of Anonymous and due to the fact that I have Anonymous turned off, it automatically drops the connection.  Is there not a way to trick this process?  So that it will prompt for the username and password?  I know that "ftp://user:@ftp.company.com" will work, but then our users complain about the "extra" work they have to do.  

Any help would be appreciated.  

Thanks in advance.

---

### Post by tturrisi on 2007-04-19
IE users can do:
[ftp://username](ftp://username) : password @ domain.com  (spaces here to prevent smilies)
They will only have to do that 1 time.  Once connected they can bookmark the site and IE6+ will retain the bookmark WITHOUT the password and each time the bookmark (or shortcut) is used IE will populate the username field in the connect prompt and the user must enter the password (unless the user clears his browser History).

If users don't want to type passwords they can export the Favorites from the IE File menu as bookmark.htm, open it in Notepad and edit the ftp url so it includes the password.  Then import back into IE.  This is insecure though as the password is plain text and anybody can read it.

You could also just create your own ftp login page at the site and have users bookmark that page.  Here's some code I made a long time ago that will work for any browser.  Note, IE browsers support ftp uploading and downloading IF the browser has FTP Folders enabled.  [http://support.microsoft.com/kb/217888](http://support.microsoft.com/kb/217888)  This cannot be done in Firefox unless a user installs the appropriate FF plugin/Extension for ftp, else FF jjust displays a list of files in the ftp dirs.
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<title>FTP Connect</title>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<script language="javascript">
function Login(form) {
var username = form.username.value;
var password = form.password.value;
var server = form.server.value;
if (username && password && server) {
var ftpsite = "ftp://" + username + ":" + password + "@" + server;
window.location = ftpsite;
}
else {
alert("Please enter your username, password, and FTP server's address.");
   }
}
</script>
</head>
<body>
<table width="100%">
<tr>
<td align="center">
<table border="0" cellpadding="3" width="450">
<tr><td>FTP Connect<br><br></td></tr>
<tr><td>Instructions:<br><br>1. Enter your username<br>2. Enter your password<br>3. Enter your Host's FTP Server as such:<i>  domain.com</i><br>4. Press Login button<br><br></td></tr></table>
<table>
<tr>
<td align="center">
<form name=login>
<table width="450" border="1" cellpadding="3">
<tr>
<td colspan="2" align=center>Login to Your FTP Server</font></td>
</tr>
<tr><td>Username</td><td><input type="text" name="username" size="24"></td></tr>
<tr><td>Password</td><td><input type="password" name="password" size="24"></td></tr>
<tr><td>Server</td><td><tt>ftp://</tt><input type="text" name="server" size="24"></td></tr>
<tr><td colspan="2" align="center"><input type="button" value="Login" onClick="Login(this.form)"></td></tr>
</table>
</form>
</td>
</tr>
</table>
<table>
<tr>
<td align="center">
<table border="0" cellpadding="3" width="450">
<tr>
<td>Help? - If cannot connect please see this <a href="http://support.microsoft.com/kb/217888" target="_new">Microsoft Article</a>.<br>If no joy then contact: <a href="mailto:admin@domain.com">admin</a>.</td></tr></table>
</td>
</tr>
</table>
</td></tr></table>
</body>
</html>

```

---

### Post by abrown1983 on 2007-04-20
That is a possibility however, we would have to open port 80 to the outside world!  I would still like to just have it prompt for the username and password!  Less ports open, safer it is :)

---

