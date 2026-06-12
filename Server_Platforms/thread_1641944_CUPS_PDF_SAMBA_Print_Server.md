---
title: "CUPS PDF SAMBA Print Server"
date: 2010-12-09
forum: Server Platforms
---

### Post by wililupy on 2010-12-09
[FONT="Arial"]I am trying to deploy an Ubuntu Linux Print Server for PDF's in our infrastructure. I have successfully installed Apache2, Samba, Cups and Cups-PDF. I can print from Unix machines and locally on the server to PDF with no problems, but when I try to connect to it via SMB or even IPP from a Windows machine, I get the following errors in the error_log:
[/FONT]
[FONT="Courier New"]D [09/Dec/2010:16:26:56 -0800] cupsdAcceptClient: 11 from localhost (Domain)
D [09/Dec/2010:16:26:56 -0800] cupsdReadClient: 11 POST /printers/printers HTTP/1.1
D [09/Dec/2010:16:26:56 -0800] cupsdSetBusyState: Active clients
D [09/Dec/2010:16:26:56 -0800] cupsdAuthorize: No authentication data provided.
D [09/Dec/2010:16:26:56 -0800] cupsdReadClient: 11 1.1 Print-Job 1
D [09/Dec/2010:16:26:56 -0800] Print-Job ipp://localhost/printers/printers
D [09/Dec/2010:16:26:56 -0800] Print-Job client-error-not-found: The printer or class was not found.
D [09/Dec/2010:16:26:56 -0800] Returning IPP client-error-not-found for Print-Job (ipp://localhost/printers/printers) from localhost
D [09/Dec/2010:16:26:56 -0800] cupsdSetBusyState: Not busy
D [09/Dec/2010:16:26:56 -0800] cupsdReadClient: 11 WAITING Closing on EOF
D [09/Dec/2010:16:26:56 -0800] cupsdCloseClient: 11
D [09/Dec/2010:16:27:00 -0800] cupsdAcceptClient: 11 from *ip.removed*:631 (IPv4)
D [09/Dec/2010:16:27:00 -0800] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1
D [09/Dec/2010:16:27:00 -0800] cupsdSetBusyState: Active clients
D [09/Dec/2010:16:27:00 -0800] cupsdAuthorize: No authentication data provided.
[/FONT]
[FONT="Arial"]In the Access_log, I get this:
[/FONT]
[FONT="Courier New"]localhost - - [09/Dec/2010:16:26:56 -0800] "POST /printers/printers HTTP/1.1" 200 288429 Print-Job client-error-not-found
[/FONT]

[FONT="Arial"]This is my cupsd.conf:
[/FONT]
[FONT="Courier New"]# Show troubleshooting information in error_log.
LogLevel debug
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Disable printer sharing and shared printers.
Browsing Off
DefaultAuthType Basic
<Location />
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>
            DefaultEncryption Never
[/FONT]

[FONT="Arial"]And this is my smb.conf:
[/FONT]

[FONT="Courier New"][global]
   workgroup = *removed*   server string = %h Print server (Samba, Ubuntu)
   wins server = *removed*   log file = /var/log/samba/log.%m
   max log size = 5000
   security = share
   load printers = yes
   printing = cups
   printcap name = cups
   socket options = TCP_NODELAY

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   create mask = 0777
   public = yes
   writeable = yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

[PDF]
   comment = Where PDF's get stored after printing
   path = /storage/PDF
   browseable = yes
   read only = no
   guest ok = yes[/FONT]

[FONT="Arial"]cups-pdf.conf file is default except AnonDirName is /storage/PDF, which is shared out via Samba and has all the proper permissions set.

I know it is an authentication issue, but I can't figure out what it needs to be to basically allow any user to print to this queue.

Thanks,
Luke
[/FONT]

---

### Post by wililupy on 2010-12-15
Got it figured out. I can't use Samba for some reason, but IPP works now. I had to make a change in /etc/apparmor.d/usr.sbin.cupsd to get it to work with my new centralized PDF export share, but now it is working fine. 

The only question I have now is there a way so that the PDF output will include the user's name in the name of the file?

I found a way to do this via a script and then share the printer via Samba that way, but it didn't work right.

I looked through the cups-pdf.conf to see if there was a way to pass ${USER} for the file name but everything keeps pointing that to a directory, which I guess would work, but I would rather it have the users name in the pdf so they can find theirs quickly and not get someone elses PDF.

I'll try looking for more information, but so far, I haven't been too successful. Perhaps cups-pdf uses a script that I can modify to append usernames to the outputted PDF name?

---

### Post by wililupy on 2010-12-15
Couldn't figure out how to append the name to the file, so we went ahead and made it so it creates a directory in the public share as the user doing the printing and put all the prints there.

I had to remove apparmor to get it to work properly since I could not figure out how to add a @{USER} variable under tunable.

I'll do some more research on apparmor but as it goes right now, this is working for me.

---

