---
title: "problem with code"
date: 2011-09-01
forum: Server Platforms
---

### Post by shubham1 on 2011-09-01
i am creating a php orject a little problem is ther
main id file
```

<?php session_start();?>
<html>
<head>
<?php
if(isset($_SESSION["lmail_id"]))
{
    mysql_connect('localhost','root','');
    mysql_select_db("lmail");
    $query=mysql_query("SELECT * FROM setting WHERE user='$_SESSION[lmail_id]' LIMIT 1");
    $set=mysql_fetch_array($query);
    $linkrel='style/' . $set['theme'];
echo "<link rel='stylesheet' type='text/css' href='$linkrel' />";
echo "<script type='text/javascript' src='function.js'></script>";    
    }
    else 
    {
        echo "<script type='text/javascript'>this.document.location.href='login.php'</script>";
        }
    ?>
</head>
<body>
    <?php
if(isset($_SESSION["lmail_id"]))
{
    echo "<span class='welcome'>welcome " . $_SESSION["lmail_id"] . "</span>";
    }
    $lab=mysql_query("SELECT * FROM label WHERE user='$_SESSION[lmail_id]'");
    echo "<br /><table class='label' boder='2px'><caption>label</caption><tr><th>name</th><th>parent folder</th></tr><br />";
        while($rlab=mysql_fetch_array($lab))
        {
            echo "<tr><td><a href='clabel.php?label=$rlab[id]' style='background-color:$rlab[color];'>"  . $rlab['name'] . "</a></td><td>" . $rlab['pfolder'] . "</td></tr>";                
            }
            echo "</table></div>";
            echo "<div id='mbody'><table id='body'><caption>mail</caption><th><input type='checkbox' id='checkall' onclick='check()' /></th><th>topic</th><th>from</th><th>date</th>";
            $inbox=mysql_query("SELECT * FROM mail WHERE pfolder = 'inbox' ORDER BY date DESC");
            while($mail=mysql_fetch_array($inbox))
            {
                       echo "<tr><td><input type='checkbox'  value='$mail[id]'  id='check' /></td><td><button type='button' value='$mail[id]' class='mail' onclick='post(" . '"readmail.php", "id=" + this.value' . " )'> " . $mail['topic'] . "</button></td><td>" . $mail['sender'] . "</td><td>" . $mail['date'] . "</td></tr>";
                }
                echo "</table></body>";
                echo "<input type='button' onclick='' style='float:right;'>new message</input>";
?>
</body>
</html>

```my javascript file
```
function post(url,fun)
{
var xmlhttp;
if (window.XMLHttpRequest)
  {
        xmlhttp=new XMLHttpRequest();
  }
else
  {
  xmlhttp=new ActiveXObject(Microsoft.XMLHTTP);
  }
xmlhttp.onreadystatechange=function()
  {
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
    document.getElementById("mbody").innerHTML=xmlhttp.responseText;
    }
  }
xmlhttp.open("POST",url,true);
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xmlhttp.send(fun);
}
```my css file
```
body
{
    background-color: #D33CB2;
color:#568068;
}
.welcome
{
color: #AF4C63;
background-color:#4CAFAD;
}
    table.label
    {
        text-align: center;
        position: absolute;
                left: 10px;
        overflow: scroll;
        width:400px;
        text-align: center;
        color: #429FA1;
        border: 2px solid red;    
                
        }
        table.label th
        {
            background-color: #78DD31;            
            }
                a:link,a:visited,a:active
        {
            text-align: center;
            text-decoration:none;
            display: block;
color: #816369;
font-weight: bold;
width:200px;
            }
            table#body
            {
                text-align: center;
                float: right;
                width:70%;
            border: 5px solid #CBCB74;                
                }
            table#body th
            {
                background-color: #D34357;
                color: #43D34C;
                }
                table#body td
                {
                    background-color: #F5F5F5;
                    color: #BD1D1D;                     
                    }
                            }
                        caption
                        {
                                        text-align: center;
font-weight: bold;
color: #C957B8;
display: block;
background-color: #C2C957;                             
                            }
                            button.mail
                            {
font-size: 10px;
color: #32E643;
background-color: #E64E32;
width:300px;
overflow: hidden;                                 
                        }
                            
    
```when i see the rrror hrought inspect elemnt of midori and epiphany it says use of undifene vairable post but is a function.

---

### Post by Wim Sturkenboom on 2011-09-01
Can you post the source of the resulting page (when loaded in browser; use menu view->source). Is easier to dig through than a mix of php and html ;)

---

### Post by shubham1 on 2011-09-02
> **Wim Sturkenboom said:**
> Can you post the source of the resulting page (when loaded in browser; use menu view->source). Is easier to dig through than a mix of php and html ;)
```
<html>
<head>
<link rel='stylesheet' type='text/css' href='style/style.css' /><script type='text/javascript' src='function.js'></script></head>
<body>
    <span class='welcome'>welcome shubham</span><br /><table class='label' boder='2px'><caption>label</caption><tr><th>name</th><th>parent folder</th></tr><br /><tr><td><a href='clabel.php?label=5' style='background-color:white;'>work</a></td><td>system</td></tr><tr><td><a href='clabel.php?label=4' style='background-color:pink;'>personal</a></td><td>system</td></tr><tr><td><a href='clabel.php?label=6' style='background-color:red;'>to do</a></td><td>system</td></tr></table></div><div id='mbody'><table id='body'><caption>mail</caption><th><input type='checkbox' id='checkall' onclick='check()' /></th><th>topic</th><th>from</th><th>date</th><tr><td><input type='checkbox'  value='6'  id='check' /></td><td><button type='button' value='6' class='mail' onclick='post("readmail.php", "id=" + this.value )'> hello</button></td><td>sid</td><td>2011-08-18 18:24:54</td></tr><tr><td><input type='checkbox'  value='3'  id='check' /></td><td><button type='button' value='3' class='mail' onclick='post("readmail.php", "id=" + this.value )'> date tesing</button></td><td>sid</td><td>2011-08-14 14:45:28</td></tr></table></body><input type='button' onclick='' style='float:right;'>new message</input></body>
</html>
```

---

### Post by shubham1 on 2011-09-02
> **shubham1 said:**
> ```
<html>
<head>
<link rel='stylesheet' type='text/css' href='style/style.css' /><script type='text/javascript' src='function.js'></script></head>
<body>
    <span class='welcome'>welcome shubham</span><br /><table class='label' boder='2px'><caption>label</caption><tr><th>name</th><th>parent folder</th></tr><br /><tr><td><a href='clabel.php?label=5' style='background-color:white;'>work</a></td><td>system</td></tr><tr><td><a href='clabel.php?label=4' style='background-color:pink;'>personal</a></td><td>system</td></tr><tr><td><a href='clabel.php?label=6' style='background-color:red;'>to do</a></td><td>system</td></tr></table></div><div id='mbody'><table id='body'><caption>mail</caption><th><input type='checkbox' id='checkall' onclick='check()' /></th><th>topic</th><th>from</th><th>date</th><tr><td><input type='checkbox'  value='6'  id='check' /></td><td><button type='button' value='6' class='mail' onclick='post("readmail.php", "id=" + this.value )'> hello</button></td><td>sid</td><td>2011-08-18 18:24:54</td></tr><tr><td><input type='checkbox'  value='3'  id='check' /></td><td><button type='button' value='3' class='mail' onclick='post("readmail.php", "id=" + this.value )'> date tesing</button></td><td>sid</td><td>2011-08-14 14:45:28</td></tr></table></body><input type='button' onclick='' style='float:right;'>new message</input></body>
</html>
```
he code will always change and the php scripthas just started preparing.more will be there.
cna you tell me some usefull php questions.

---

### Post by 11notes on 2011-09-02
First: you write awfull code, never mix php with html, its just terible!
Second:

you try to xmp rcp with : onclick='post(" . '"readmail.php", "id=" + this.value' . " )'> " that's never going to work because xml rpc only works by POST not GET! you need to hand over the variable to the POST body of your xml rpc and then catch it with $_POST

---

### Post by shubham1 on 2011-09-02
> **11notes said:**
> First: you write awfull code, never mix php with html, its just terible!
Second:

you try to xmp rcp with : onclick='post(" . '"readmail.php", "id=" + this.value' . " )'> " that's never going to work because xml rpc only works by POST not GET! you need to hand over the variable to the POST body of your xml rpc and then catch it with $_POST
look at this
what  iam trying to do
first parameter for file name and second for the  request to be send
function post(url,fun) { var xmlhttp; if (window.XMLHttpRequest)   {         xmlhttp=new XMLHttpRequest();   } else   {   xmlhttp=new ActiveXObject(Microsoft.XMLHTTP);   } xmlhttp.onreadystatechange=function()   {   if (xmlhttp.readyState==4 && xmlhttp.status==200)     {     document.getElementById("mbody").innerHTML=xmlhttp.responseText;     }   } xmlhttp.open("POST",url,true); xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded"); xmlhttp.send(fun); }

---

### Post by shubham1 on 2011-09-02
> **11notes said:**
> First: you write awfull code, never mix php with html, its just terible!
Second:

you try to xmp rcp with : onclick='post(" . '"readmail.php", "id=" + this.value' . " )'> " that's never going to work because xml rpc only works by POST not GET! you need to hand over the variable to the POST body of your xml rpc and then catch it with $_POST
some times the script becomes colpicated but we have to deal with it.the porblem is of quotes there are only 2 but see
for eg.
echo "<span onlick='xyz_***(here two parameters are to bes insterted with ***_'')'";

---

### Post by shubham1 on 2011-09-02
> **11notes said:**
> First: you write awfull code, never mix php with html, its just terible!
Second:

you try to xmp rcp with : onclick='post(" . '"readmail.php", "id=" + this.value' . " )'> " that's never going to work because xml rpc only works by POST not GET! you need to hand over the variable to the POST body of your xml rpc and then catch it with $_POST
i know that a got the code from [http://www.w3schools.com](http://www.w3schools.com)
post has to be display a set header request
and get the url is there
as it is like this in case of get
link.php?link=2
just for example.

---

