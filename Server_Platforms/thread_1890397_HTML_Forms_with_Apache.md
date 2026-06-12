---
title: "HTML Forms with Apache"
date: 2011-12-03
forum: Server Platforms
---

### Post by createdcreature on 2011-12-03
How do I set up HTML forms with Apache? Here is the code. How would I set this up?

**Content of echo.pl**

#!C:/Perl/bin/perl                                


  if ($ENV{'REQUEST_METHOD'} eq 'GET') 
  {                                                  
    @pairs = split(/&/, $ENV{'QUERY_STRING'});              
  }                                                   
  elsif ($ENV{'REQUEST_METHOD'} eq 'POST') 
  {                                                    
    read (STDIN, $buffer, $ENV{'CONTENT_LENGTH'});                             
    @pairs = split(/&/, $buffer);                          
    if ($ENV{'QUERY_STRING'}) 
    {                            
      @getpairs =split(/&/, $ENV{'QUERY_STRING'}); 
      push(@pairs,@getpairs);   
    }                                                       
  }                                                    
  else 
  {                                               
    print "Content-type:text/html\n\n";                 
    print "Unrecognized Request Method - Use GET or POST.";
  }                                                                                                     

  foreach $pair (@pairs) 
  {                                                  
    ($key, $value) = split(/=/, $pair);                  
    $key =~ tr/+/ /;                                     
    $key =~ s/%(..)/pack("c", hex($1))/eg;             
    $value =~ tr/+/ /;                                   
    $value =~ s/%(..)/pack("c", hex($1))/eg;           
    $value =~s/<!--(.|\n)*-->//g;  # ignore SSI
    if ($formdata{$key}) 
    {                                         
      $formdata{$key} .= ", $value";                          
    }                                                    
    else 
    { 
    $formdata{$key} = $value; 
    }                                
  }                                                   

$num=1;
print "Content-Type: text/html\n\n<!DOCTYPE HTML>\n\n<html lang=\"en\">\n\n";
print "<head>\n<meta charset=\"UTF-8\">\n<title>Web Server Response</title>\n";
print "<link rel=\"stylesheet\" href=\"echo.css\">\n</head>\n\n<body>\n";
print "<table>\n<caption><img src=\"perl.png\"></caption>\n";
print "<colgroup><col class=\"no\"><col><col></colgroup>\n";
print "<thead><tr><th>Pair No.<th>Name<th>Value</tr></thead>\n";
print "<tfoot><tr><td colspan=\"3\"><img src=\"abyss.png\"></tr></tfoot>\n<tbody>\n";
foreach $key (sort (keys %formdata))
{
	print "<tr";
	if($num%2 == 0){print " class=\"stripe\""};
	print "><td>$num<td>$key<td>$formdata{$key}</tr>\n"; 
	$num++;
}    
print "</tbody>\n</table>\n</body>\n\n</html>";

**Content of submit.html**

<!DOCTYPE HTML>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Form Submission Example</title>
</head>
<body>
<form method="GET" action="http://localhost/echo.pl" >
<p>
<input type="submit" name="My Submit Button Name" value="My Submit Button Value">
<p>
</form>
</body>
</html>

**Two files named abyss.png and perl.png are in a 'htdocs' directory of the web server, along with echo.pl.**

---

### Post by createdcreature on 2011-12-06
How should I do this? I want to see the result of the form people are clicking, but on MY web server running Apache2 with Ubuntu 10.04 LTS.

---

### Post by SeijiSensei on 2011-12-06
Take a look at [mod_perl]("http://perl.apache.org/") perhaps, or set up a [cgi-bin]("http://httpd.apache.org/docs/current/howto/cgi.html") configuration.  I suspect the mod_perl route is the easier one, but since I use PHP, I can't help much beyond this.

As for getting the output, the easiest method is to mail it to yourself.

---

### Post by createdcreature on 2011-12-07
Would I be able to do this with PHP? I would prefer PHP as well.

---

### Post by SeijiSensei on 2011-12-08
> **Robert Moyse said:**
> Would I be able to do this with PHP? I would prefer PHP as well.

Sure.  A quick Google search for "forms processing php" brought up a number of tutorials.

---

