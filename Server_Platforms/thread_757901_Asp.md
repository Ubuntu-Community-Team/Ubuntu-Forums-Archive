---
title: "Asp"
date: 2008-04-17
forum: Server Platforms
---

### Post by blippy on 2008-04-17
The company where I work has recently switched to a Windows server, and has a static website written in ASP. It all works. I know practically nothing about ASP, other than its like HTML but you can do dynamic stuff with it. I am a programmer, though.

What's the difference between ASP and ASPX, anyway? 

I've been asked to do a bit of dynamic content generation using ASP (VBScript, no databases involved). I downloaded MS Web Developer 2005 Express on XP, or something, and it seems that the ASP is incompatible with ASPX. Way to go, Microsoft.

I tried poking around with various things, and figured I'd have a go at seeing if Linux could do it better. I'm using Gutsy (soon Hardy!!) Desktop, and installed a whole bunch of Apache2/Mono stuff.

I found an example of an ASP script, and put it in /var/www:
> 
<script runat="server">
Sub submit(sender As Object, e As EventArgs)
lbl1.Text="Your name is " & txt1.Text
End Sub
</script>

<html>
<body>

<form runat="server">
Enter your name:
<asp:TextBox id="txt1" runat="server" />
<asp:Button OnClick="submit" Text="Submit" runat="server" />
<p><asp:Label id="lbl1" runat="server" /></p>
</form>

</body>
</html>

but when I do
[http://localhost/foo.asp](http://localhost/foo.asp)
Apache just displays the script without actually running it. :( Looks live I've got mod_mono set up for Apache to me, It's in mods-enabled and everything. Can anyone suggest what trick I might be missing?

---

### Post by jonabyte on 2008-04-17
not sure if you need to do something to the conf file or add to read asp type files.

aspx is .net version, asp is not, both have/use different features

---

