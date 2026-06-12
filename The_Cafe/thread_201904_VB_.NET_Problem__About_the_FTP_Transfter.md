---
title: "VB .NET Problem ??????? About the FTP Transfter"
date: 2006-06-22
forum: The Cafe
---

### Post by 008325 on 2006-06-22
```
        
Values to use
Const localFile As String = "C:\myfile.bin"
Const remoteFile As String = "/pub/myftpfile.bin"
Const host As String = "ftp://ftp.myhost.com"
Const username As String = "myuserid"
Const password As String = "mypassword"

'1. Create a request: must be in ftp://hostname format, 
'   not just ftp.myhost.com
Dim URI As String = host & remoteFile
Dim ftp As System.Net.FtpWebRequest = _
    CType(FtpWebRequest.Create(URI), FtpWebRequest)

'2. Set credentials
ftp.Credentials = New _
    System.Net.NetworkCredential(username, password)

'3. Settings and action
ftp.KeepAlive = False
'we want a binary transfer, not textual data
ftp.UseBinary = True
'Define the action required (in this case, download a file)
ftp.Method = System.Net.WebRequestMethods.Ftp.DownloadFile

'4. If we were using a method that uploads data e.g. UploadFile
'   we would open the ftp.GetRequestStream here an send the data

'5. Get the response to the Ftp request and the associated stream
Using response As System.Net.FtpWebResponse = _
      CType(ftp.GetResponse, System.Net.FtpWebResponse)
  Using responseStream As IO.Stream = response.GetResponseStream
    'loop to read & write to file
    Using fs As New IO.FileStream(localFile, IO.FileMode.Create)
      Dim buffer(2047) As Byte
      Dim read As Integer = 0
      Do
        read = responseStream.Read(buffer, 0, buffer.Length)
        fs.Write(buffer, 0, read)
      Loop Until read = 0 'see Note(1)
      responseStream.Close()
      fs.Flush()
      fs.Close()
    End Using
    responseStream.Close()
  End Using
  response.Close()
End Using

'6. Done! the Close happens because ftp goes out of scope
'   There is no .Close or .Dispose for FtpWebRequest
```

i copy this code from the code project 
but this code is for downloading file...
how can i change this code for uploading file ?

i am just a newbie .....plx help 

:( :(

---

### Post by 008325 on 2006-06-22
Please Help..really urgent

---

### Post by bruce89 on 2006-06-22
Shouldn't this be in the coding forum? - [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Stone123 on 2006-06-22
Use sockets for that , i dont think ftp class in vb.net is for that.
pseudocode:

while 1 :

Dim s As Socket= = ConnectSocket(client, port)
listen on port
..
when request : 

s.Send(bytesSent, bytesSent.Length, 0)

and read some book.

---

### Post by 008325 on 2006-06-22
[QUOTE=Stone123]Use sockets for that , i dont think ftp class in vb.net is for that.
pseudocode:

while 1 :

Dim s As Socket= = ConnectSocket(client, port)
listen on port
..
when request : 

s.Send(bytesSent, bytesSent.Length, 0)

and read some book.[/QUOTE]

i dont know too much , but i read this 

[http://www.codeproject.com/vb/net/FtpClient.asp](http://www.codeproject.com/vb/net/FtpClient.asp)

---

### Post by 008325 on 2006-06-23
push

---

