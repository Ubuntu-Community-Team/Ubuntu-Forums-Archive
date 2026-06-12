---
title: "Fixing FTP with /var/www"
date: 2017-05-20
forum: Server Platforms
---

### Post by aerexos on 2017-05-20
I would like to setup SFTP or FTP. I am trying to access my "/var/www/" files from FTP. 
Here is my VB code (What I need it for) 
```
Dim request As FtpWebRequest = DirectCast(WebRequest.Create("ftp://example.com//var/www/html/"), FtpWebRequest)
```
So, I want to be able to view these files from the browser. Like "ftp://example.com/var/www/html/".
I don't really care if I could get hacked in 20 seconds or so. 

I just want this to be able to work. Please can someone link me the answer, I've looked for hours and hours and I have not found a thing.

Its only a VPS anyway, I can just reset with a click of a button and there is no important data stored on it. The password is different to all my others.
I'm using ubuntu 14.04

Everytime I try use FTP with my root user it decides to allow the login, but request a login again straight after?
I use this tutorial to set mine up;
[http://www.krizna.com/ubuntu/setup-ftp-server-on-ubuntu-14-04-vsftpd/](http://www.krizna.com/ubuntu/setup-ftp-server-on-ubuntu-14-04-vsftpd/)
But I can't get access to /var/www

Here is my code in VB if it helps
```
    Private Sub Button9_Click(sender As Object, e As EventArgs) Handles Button9.Click
        RTBadmin.Text = ""
        Try
            Dim request As System.Net.FtpWebRequest = DirectCast(System.Net.WebRequest.Create("ftp://example.com/var/www/html/" + TBfilename.Text), System.Net.FtpWebRequest)
            request.Credentials = New System.Net.NetworkCredential("???", "???")
            request.Method = System.Net.WebRequestMethods.Ftp.UploadFile


            Dim file() As Byte = System.IO.File.ReadAllBytes(TBpath.Text)


            Dim strz As System.IO.Stream = request.GetRequestStream()
            strz.Write(file, 0, file.Length)
            strz.Close()
            strz.Dispose()
            RTBadmin.Text = RTBadmin.Text + Date.Now.ToString("yyyy/MM/dd HH:mm:ss") + ": Upload Complete."
        Catch
            RTBadmin.Text = ""
            RTBadmin.Text = RTBadmin.Text + Date.Now.ToString("yyyy/MM/dd HH:mm:ss") + ": Upload Failed."
        End Try
    End Sub
```
I need to be able to upload my files to that directory, using this code. Someone help please.

:(

---

### Post by TheFu on 2017-05-21
Welcome to the forums.

I wouldn't do it the way described above.

I'd use ssh and either scp, rsync or sftp.  Since I don't use Windows much, rsync+ssh is my default solution for moving more than 1 file.  **rsync** uses ssh by default.

Plain FTP should have died in 1994.

I don't know anything about VB.  Putty has pscp.  Filezilla supports sftp.  I doubt VB can use sftp easily. Probably need a 3rd party library.  Plus using ssh-keys is one of the things I love about ssh-based solutions.  Being both MORE secure AND more convenient than other options.

Your system being hacked is a danger to the rest of the world. We care, even if you don't.

---

### Post by aerexos on 2017-05-21
yeah but tbh, like I said before, I dont care which the best method I'd like to use the one stated above.

---

### Post by waqt on 2017-05-22
Install Pure-FTP, instructions here: [https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

Just make sure that when you declare the user directory it's /var/www/html/:
```

sudo pure-pw useradd **joe** -u ftpuser -d /var/www/html/
```


Then you code will change to:


```
Dim request As System.Net.FtpWebRequest = DirectCast(System.Net.WebRequest.Create("ftp://example.com/" + TBfilename.Text), System.Net.FtpWebRequest)
```

---

