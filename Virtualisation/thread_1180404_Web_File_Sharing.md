---
title: "Web File Sharing"
date: 2009-06-06
forum: Virtualisation
---

### Post by andrei.kouznetsov on 2009-06-06
I am not sure that this question should be asked here, but I will try.

Here is my situation.
I have ubuntu 9.04 and Windows XP in kvm (kernel virtual machine).
Using kvm option of redirecting ports, I can redirect some incoming connections to my virtual machine. So, I start kvm with the option
```
-redir tcp:5555::80
```
it forwards my local port 5555 to the port 80 on the virtual machine. In windows I share a folder using Web File Sharing (the name of this folder is "public"). Now, if I start Firefox in Ubuntu and type in the URL
```
http://localhost:5555/public
```
I can browse the folder "public" and view the files. However, If I use
Places>Connect to server>WebDAV, then it says "access denied". When I try mount.davfs, it does not say any error, but I can not see the folder either.

Do I miss something? Why does not it work?

---

### Post by andrei.kouznetsov on 2009-06-08
Any ideas?

---

### Post by andrei.kouznetsov on 2009-06-14
Here is more information.

I used WireShark on my virtual machine to find out what is going on when I connect to the shared folder. So, here is the log:

Nautilus sends:
```

OPTIONS /public HTTP/1.1
Host: localhost:5555
User-Agent: gvfs/1.2.2

```

Windows responds
```

HTTP/1.1 401 Access Denied
Server: Microsoft-IIS/5.1
Date: Mon, 15 Jun 2009 00:42:42 GMT
WWW-Authenticate: Negotiate
WWW-Authenticate: NTLM
Connection: close
Content-Length: 4431
Content-Type: text/html

```

and the body of the response is
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html dir=ltr>

<head>
<style>
a:link                  {font:8pt/11pt verdana; color:FF0000}
a:visited               {font:8pt/11pt verdana; color:#4e4e4e}
</style>

<META NAME="ROBOTS" CONTENT="NOINDEX">

<title>You are not authorized to view this page</title>

<META HTTP-EQUIV="Content-Type" Content="text-html; charset=Windows-1252">
</head>

<script> 
function Homepage(){
<!--
// in real bits, urls get returned to our script like this:
// res://shdocvw.dll/http_404.htm#http://www.DocURL.com/bar.htm 

//For testing use DocURL = "res://shdocvw.dll/http_404.htm#https://www.microsoft.com/bar.htm"
DocURL=document.URL;

//this is where the http or https will be, as found by searching for :// but skipping the res://
protocolIndex=DocURL.indexOf("://",4);

//this finds the ending slash for the domain server 
serverIndex=DocURL.indexOf("/",protocolIndex + 3);

//for the href, we need a valid URL to the domain. We search for the # symbol to find the begining 
//of the true URL, and add 1 to skip it - this is the BeginURL value. We use serverIndex as the end marker.
//urlresult=DocURL.substring(protocolIndex - 4,serverIndex);
BeginURL=DocURL.indexOf("#",1) + 1;
urlresult=DocURL.substring(BeginURL,serverIndex);

//for display, we need to skip after http://, and go to the next slash
displayresult=DocURL.substring(protocolIndex + 3 ,serverIndex);
InsertElementAnchor(urlresult, displayresult);
}

function HtmlEncode(text)
{
    return text.replace(/&/g, '&amp').replace(/'/g, '&quot;').replace(/</g, '&lt;').replace(/>/g, '&gt;');
}

function TagAttrib(name, value)
{
    return ' '+name+'="'+HtmlEncode(value)+'"';
}

function PrintTag(tagName, needCloseTag, attrib, inner){
    document.write( '<' + tagName + attrib + '>' + HtmlEncode(inner) );
    if (needCloseTag) document.write( '</' + tagName +'>' );
}

function URI(href)
{
    IEVer = window.navigator.appVersion;
    IEVer = IEVer.substr( IEVer.indexOf('MSIE') + 5, 3 );

    return (IEVer.charAt(1)=='.' && IEVer >= '5.5') ?
        encodeURI(href) :
        escape(href).replace(/%3A/g, ':').replace(/%3B/g, ';');
}

function InsertElementAnchor(href, text)
{
    PrintTag('A', true, TagAttrib('HREF', URI(href)), text);
}

//-->
</script>

<body bgcolor="FFFFFF">

<table width="410" cellpadding="3" cellspacing="5">

  <tr>    
    <td align="left" valign="middle" width="360">
<h1 style="COLOR:000000; FONT: 13pt/15pt verdana"><!--Problem-->You are not authorized to view this page</h1>
    </td>
  </tr>
  
  <tr>
    <td width="400" colspan="2">
<font style="COLOR:000000; FONT: 8pt/11pt verdana">You do not have permission to view this directory or page using the credentials you supplied.</font></td>
  </tr>
  
  <tr>
    <td width="400" colspan="2">
<font style="COLOR:000000; FONT: 8pt/11pt verdana">

<hr color="#C0C0C0" noshade>

   <p>Please try the following:</p>
   
<ul>
<li>Click the <a href="javascript:location.reload()">Refresh</a> button to try again with different credentials.</li>

<li>If you believe you should be able to view this directory or page, please contact the Web site administrator by using the e-mail address or phone number listed on the 

<script> 
<!--
if (!((window.navigator.userAgent.indexOf("MSIE") > 0) && (window.navigator.appVersion.charAt(0) == "2")))
{
Homepage();
}
//-->
</script>
home page.</li>
</ul>

    <h2 style="font:8pt/11pt verdana; color:000000">HTTP 401.2 - Unauthorized: Logon failed due to server configuration<br>
    Internet Information Services</h2>

<hr color="#C0C0C0" noshade>

<p>Technical Information (for support personnel)</p>
<ul>

<li>Background:<br>
This is usually caused by a server-side script not sending the proper WWW-Authenticate header field. Using Active Server Pages scripting this is done by using the <strong>AddHeader</strong> method of the <strong>Response</strong> object to request that the client use a certain authentication method to access the resource.

<p>
<li>More information:<br>
<a href="http://www.microsoft.com/ContentRedirect.asp?prd=iis&sbp=&pver=5.0&pid=&ID=401.2&cat=web&os=&over=&hrd=&Opt1=&Opt2=&Opt3=" target="_blank">Microsoft Support</a>
</li>
</p>
</ul> 

</font></td>
  </tr>
  
</table>
</body>
</html>

```

I wonder how I can fix this :(

---

