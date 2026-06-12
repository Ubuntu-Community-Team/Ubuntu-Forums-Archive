---
title: "MS Exchange Server Read from Linux"
date: 2009-10-16
forum: Server Platforms
---

### Post by davigre on 2009-10-16
Hi, 

I need to retrieve (only read) the contacts directory from a MS Exchange Server from Linux. The idea is to use php or Java servlet. 

Does someone knows how to make this ?

Thanks you all.

David.

---

### Post by drumbug1 on 2009-10-16
I'm assuming you mean pulling your GAL (Global Address List) from Active Directory (this information is not actually in "Exchange" but rather in Active Directory... which integrates with Exchange).

I've done this on a intranet site using the software from this site:

[http://adldap.sourceforge.net/](http://adldap.sourceforge.net/)

My purpose is probably different than what you're trying to do, but I pull the currently logged in users' username and e-mail from AD with this code:

```

// Query the Active Directory
$result=$ldap->authenticate($_POST["username"],$_POST["password"]);

// Query the Active Directory for the displayname
$userinfo = $ldap->user_info($_POST["username"],array("displayname"));
$fullname = $userinfo[0][displayname][0];
$usermail = $ldap->user_info($_POST["username"],array("mail"));
$mailname = $usermail[0][mail][0];

```

...then I can dump it into a session variable and work with it.

In another area I've got code to create a drop-down list with all users in a distribution list.  You should be able to modify this to pull a list of all e-mails in a particular distribution list, etc:

```

include ("../../adLDAP/adLDAP.php");
try {
    $ldap = new adLDAP($options);
}
catch (adLDAPException $e) {
    echo $e; exit();
}

        $result=$ldap->authenticate("webappusername","webapppassword");


        // Pull the Full User info from AD
        $result=$ldap->group_info("My Dist List",array("member"));
        $barf = $result[0][member];

        // Put values into new array with text processing
        $newarray = array();
        foreach ($barf as $key => $value)
        {
        $newarray[]=substr($value,3, strpos($value, ',')-3);
        };

        // Alphabetize the array
        $sorted = asort($newarray);

        // Create Select Box
        echo '<SELECT name=user>';
        foreach ($newarray as $key => $value)
        {
        echo '<OPTION value="'.$value.'"> '.$value.'';
        }
        echo '</select><br>';}

        else {
        echo $_SESSION["displayname"];
        }

```

Hope this points you in the right direction....  :-)

---

### Post by davigre on 2009-10-19
Thank You a lot !!! I will try your ideas and tell. I think you were right with the GAL information.

bye.

David.

---

