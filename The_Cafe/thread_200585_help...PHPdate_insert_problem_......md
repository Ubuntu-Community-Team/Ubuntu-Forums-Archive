---
title: "help...PHP/date insert problem ....."
date: 2006-06-20
forum: The Cafe
---

### Post by 008325 on 2006-06-20
m_day and m_month are the list box , m_year is text box 

i tired these code to insert the date 

[PHP]$date_value=$m_year.'-'.$m_month.'-'.$m_day;[/PHP]

or 
[PHP]
$date_value="$m_year-$m_month-$m_day";[/PHP]

both can not insert the date into MYSQL

how can i slove this problem ?

thx

---

### Post by 008325 on 2006-06-20
please ......

---

### Post by v8YKxgHe on 2006-06-20
Are you sure the MySQL field type is set to Varchar? Also does it give you an error when you try to insert it into the database - please post your entire sql Query too =)

---

### Post by 008325 on 2006-06-20
[QUOTE=AlexC_]Are you sure the MySQL field type is set to String? Also does it give you an error when you try to insert it into the database - please post your entire sql Query too =)[/QUOTE]

actually , i set to date format @@

however , i dont think this is a type problem

bez i set it to varchat

it got "--" in the birthday column -.-

---

### Post by v8YKxgHe on 2006-06-20
I've never used the date field type. When ever I store dates in a SQL table I do this ( with the field as integer )

[PHP]
$time = time();
$Query = mysql_query( " INSERT INTO tablename ( timeStamp ) VALUES ( '$time ) " );

[/PHP]

Then when I want to output it, I use the date() php function, eg

[PHP]
$Query = mysql_query( " SELECT * FROM tablename " );
$result = mysql_fetch_array( $Query );

$date = date( "Y-M-D", $result['timeStamp'] );
echo $date;
[/PHP]

I think that should work, I find it easier to store it the Unix timestamp way because you can easily change the way the date is formated afterwards. [http://uk2.php.net/date](http://uk2.php.net/date)

---

### Post by 008325 on 2006-06-20
> **AlexC_]I've never used the date field type. When ever I store dates in a SQL table I do this ( with the field as integer )

[PHP]
$time = time() said:**
> 

Then when I want to output it, I use the date() php function, eg

[PHP]
$Query = mysql_query( " SELECT * FROM tablename " );
$result = mysql_fetch_array( $Query );

$date = date( "Y-M-D", $result['timeStamp'] );
echo $date;
[/PHP]

I think that should work, I find it easier to store it the Unix timestamp way because you can easily change the way the date is formated afterwards. [http://uk2.php.net/date](http://uk2.php.net/date)

um....however , i set it to the varchar , it just can get "--" in the database

i think that the php can not get the value ? is it ?

[HTML]	  <tr>
	  <td align="right">Birthday</td>
        <td><font>*</font></td>
	   <td align="left">
	   <select name="m_day">
								<option value="01" >1</option>
								<option value="02" >2</option>
								<option value="03" >3</option>
								<option value="04" >4</option>
								<option value="05" >5</option>
								<option value="06" >6</option>
								<option value="07" >7</option>
								<option value="08" >8</option>
								<option value="09" >9</option>
								<option value="10" >10</option>
								<option value="11" >11</option>
								<option value="12" >12</option>
								<option value="13" >13</option>
								<option value="14" >14</option>
								<option value="15" >15</option>
								<option value="16" >16</option>
								<option value="17" >17</option>
								<option value="18" >18</option>
								<option value="19" >19</option>
								<option value="20" >20</option>
								<option value="21" >21</option>
								<option value="22" >22</option>
								<option value="23" >23</option>
								<option value="24" >24</option>
								<option value="25" >25</option>
								<option value="26" >26</option>
								<option value="27" >27</option>
								<option value="28" >28</option>
								<option value="29" >29</option>
								<option value="30" >30</option>
								<option value="31" >31</option>
							</select>
	     <select name="m_month">
           <option value="01" >January</option>
           <option value="02" >February</option>
           <option value="03" >March</option>
           <option value="04" >April</option>
           <option value="05" >May</option>
           <option value="06" >June</option>
           <option value="07" >July</option>
           <option value="08" >August</option>
           <option value="09" >September</option>
           <option value="10" >October</option>
           <option value="11" >November</option>
           <option value="12" >December</option>
         </select>
		<input type="text" name="m_year" value="" size="4" maxlength="4" />
	  </tr>
      <tr>[/HTML]

---

### Post by v8YKxgHe on 2006-06-20
Can you please post your entire PHP code for it so I can look over it?


Edit, No I see your problem. You have no <form> tags

[HTML]
	  <tr>
	  <td align="right">Birthday</td>
        <td><font>*</font></td>
	   <td align="left">
<-- You needed this form action -->
<form action="URL HERE" method="post" enctype="multipart/form-data">

	   <select name="m_day">
								<option value="01" >1</option>
								<option value="02" >2</option>
								<option value="03" >3</option>
								<option value="04" >4</option>
								<option value="05" >5</option>
								<option value="06" >6</option>
								<option value="07" >7</option>
								<option value="08" >8</option>
								<option value="09" >9</option>
								<option value="10" >10</option>
								<option value="11" >11</option>
								<option value="12" >12</option>
								<option value="13" >13</option>
								<option value="14" >14</option>
								<option value="15" >15</option>
								<option value="16" >16</option>
								<option value="17" >17</option>
								<option value="18" >18</option>
								<option value="19" >19</option>
								<option value="20" >20</option>
								<option value="21" >21</option>
								<option value="22" >22</option>
								<option value="23" >23</option>
								<option value="24" >24</option>
								<option value="25" >25</option>
								<option value="26" >26</option>
								<option value="27" >27</option>
								<option value="28" >28</option>
								<option value="29" >29</option>
								<option value="30" >30</option>
								<option value="31" >31</option>
							</select>
	     <select name="m_month">
           <option value="01" >January</option>
           <option value="02" >February</option>
           <option value="03" >March</option>
           <option value="04" >April</option>
           <option value="05" >May</option>
           <option value="06" >June</option>
           <option value="07" >July</option>
           <option value="08" >August</option>
           <option value="09" >September</option>
           <option value="10" >October</option>
           <option value="11" >November</option>
           <option value="12" >December</option>
         </select>
		<input type="text" name="m_year" value="" size="4" maxlength="4" />
</form>
	  </tr>
      <tr>

[/HTML]

Edit ( Again ):

Then to recieve your data you need to do:

[PHP]
$mDay = $_POST['m_day'];
$mMonth = $_POST['m_month'];
$mYear = $_POST['m_year'];
[/PHP]

---

### Post by 008325 on 2006-06-20
[QUOTE=AlexC_]Can you please post your entire PHP code for it so I can look over it?


Edit, No I see your problem. You have no <form> tags[/QUOTE]

it just a part ....sorry , i post th whole code ^^

[HTML]<?php require_once('Connection/conn.php'); ?>
<?php include('top.php'); ?>
<?php 
			if (isset($_POST['addrecord'])) {
			
					if (trim($_FILES['resueme_file']['name']) != "") {
					$File_Extension = explode(".", $_FILES['resueme_file']['name']);
					$File_Extension = $File_Extension[count($File_Extension)-1];
					$ServerFilename =date("YmdHis") . "." . $File_Extension;
					  move_uploaded_file($_FILES['resueme_file']['tmp_name'], file."/".$ServerFilename);
					 $error="false"; 
					$date_value=$m_year.'-'.$m_month.'-'.$m_day;

					mysql_select_db($database_human, $connecthuman);
  					$query = sprintf("INSERT INTO job(Name,Gender,Education,Graduate_From,Birthday,Experience,Last_Apply_Dept,File) VALUES 			('%s','%s','%s','%s','%s','%s','%s','%s')",$_POST['app_name'],$_POST['select_gender'],$_POST['select_Education'],$_POST['Gradudate_From'],$date_value,$_POST['app_exp'],$_POST['app_dept'],$ServerFilename);

  					$Result = mysql_query($query, $connecthuman) or die(mysql_error());
					
				   	}
					
					else {
					$error="true";
					}
			}
?>
<tr height="100%" valign="top"> 
  <td height="100%" valign="top">
  <form action="add_record.php" id="form1" name="form1" method="POST" enctype="multipart/form-data">
  <table cellpadding="2" cellspacing="1" width="46%" align="center">
    <tbody>
      <tr>
        <td colspan="3" class="RegSectionTitle"><div align="center">Add Applicator  Form </div>
          <hr noshade="noshade" size="1" /></td>
      </tr>
	     <tr>
        <td align="right">Name</td>
        <td><font>*</font></td>
        <td align="left">
		<input name="app_name" type="text" value="" /></td>
      </tr>
	        <tr>
        <td align="right">Gender</td>
        <td><font>*</font></td>
        <td align="left"><label>
          <select name="select_gender">
		     <option value="Male" selected="selected" >Male</option>
		  <option value="Female" >Female</option>
          </select>
        </label></td>
      </tr>
      <tr>
        <td align="right">Education</td>
        <td><font>*</font></td>
        <td align="left"><select name="select_Education">
          <option value="University" selected="selected" >University</option>
		  <option value="Polytechnic" >Polytechnic</option>
          <option value="High school" >High school</option>
          <option value="Primary school" >Primary school</option>
		  <option value="None" >None</option>
        </select></td>
      </tr>
      <tr>
        <td align="right">Gradudate From </td>
        <td><font>*</font></td>
        <td align="left"><label>
        <input name="Gradudate_From" type="text" value="" />
        </label></td>
      </tr>
	  <tr>
	  <td align="right">Birthday</td>
        <td><font>*</font></td>
	   <td align="left">
	   <select name="m_day">
								<option value="01" >1</option>
								<option value="02" >2</option>
								<option value="03" >3</option>
								<option value="04" >4</option>
								<option value="05" >5</option>
								<option value="06" >6</option>
								<option value="07" >7</option>
								<option value="08" >8</option>
								<option value="09" >9</option>
								<option value="10" >10</option>
								<option value="11" >11</option>
								<option value="12" >12</option>
								<option value="13" >13</option>
								<option value="14" >14</option>
								<option value="15" >15</option>
								<option value="16" >16</option>
								<option value="17" >17</option>
								<option value="18" >18</option>
								<option value="19" >19</option>
								<option value="20" >20</option>
								<option value="21" >21</option>
								<option value="22" >22</option>
								<option value="23" >23</option>
								<option value="24" >24</option>
								<option value="25" >25</option>
								<option value="26" >26</option>
								<option value="27" >27</option>
								<option value="28" >28</option>
								<option value="29" >29</option>
								<option value="30" >30</option>
								<option value="31" >31</option>
							</select>
	     <select name="m_month">
           <option value="01" >January</option>
           <option value="02" >February</option>
           <option value="03" >March</option>
           <option value="04" >April</option>
           <option value="05" >May</option>
           <option value="06" >June</option>
           <option value="07" >July</option>
           <option value="08" >August</option>
           <option value="09" >September</option>
           <option value="10" >October</option>
           <option value="11" >November</option>
           <option value="12" >December</option>
         </select>
		<input type="text" name="m_year" value="" size="4" maxlength="4" />
	  </tr>
      <tr>
        <td align="right">Working Experience</td>
        <td><font>*</font></td>
        <td align="left">
		<input name="app_exp" value="" type="text" /></td>
      </tr>
      <tr>
        <td align="right">Last Apply Dept</td>
        <td><font>*</font></td>
        <td align="left">
		<input name="app_dept" type="text" value=""  /></td>
      </tr>

	        <tr>
        <td align="right">Resume</td>
        <td><font>*</font></td>
        <td align="left">
		<input type="file" name="resueme_file" size="30" value=""></td>
      </tr>
	  
	  
    </tbody>
	
    <tbody>
      <tr>
        <td colspan="2">&nbsp;</td>
        <td><input type="submit" name="Submit" value="Submit" /></td>
      </tr>
    </tbody>
  </table>
 <input type="hidden" name="addrecord" value="form1">
</form>
<div align="center"><?php if ( $error == "true" ) { echo "Fail to Add Record "; } elseif ( $error == "false" ) { echo "Add Record Sccussful"; }?></div>
  </td>
</tr>
<?php include('bottom.php'); ?>
[/HTML]

---

### Post by v8YKxgHe on 2006-06-20
Sorry to be a pain, but could you post that code on [http://pastebin.ca/](http://pastebin.ca/) and then give me the URL it gives you? Trying to read it in that small box is a pain, and if I copy it to my PHP IDE it's all on one line and a pain to rea.

---

### Post by 008325 on 2006-06-20
> **AlexC_]Can you please post your entire PHP code for it so I can look over it?


Edit, No I see your problem. You have no <form> tags

[HTML]
	  <tr>
	  <td align="right">Birthday</td>
        <td><font>*</font></td>
	   <td align="left">
<-- You needed this form action -->
<form action="URL HERE" method="post" enctype="multipart/form-data">

	   <select name="m_day">
								<option value="01" >1</option>
								<option value="02" >2</option>
								<option value="03" >3</option>
								<option value="04" >4</option>
								<option value="05" >5</option>
								<option value="06" >6</option>
								<option value="07" >7</option>
								<option value="08" >8</option>
								<option value="09" >9</option>
								<option value="10" >10</option>
								<option value="11" >11</option>
								<option value="12" >12</option>
								<option value="13" >13</option>
								<option value="14" >14</option>
								<option value="15" >15</option>
								<option value="16" >16</option>
								<option value="17" >17</option>
								<option value="18" >18</option>
								<option value="19" >19</option>
								<option value="20" >20</option>
								<option value="21" >21</option>
								<option value="22" >22</option>
								<option value="23" >23</option>
								<option value="24" >24</option>
								<option value="25" >25</option>
								<option value="26" >26</option>
								<option value="27" >27</option>
								<option value="28" >28</option>
								<option value="29" >29</option>
								<option value="30" >30</option>
								<option value="31" >31</option>
							</select>
	     <select name="m_month">
           <option value="01" >January</option>
           <option value="02" >February</option>
           <option value="03" >March</option>
           <option value="04" >April</option>
           <option value="05" >May</option>
           <option value="06" >June</option>
           <option value="07" >July</option>
           <option value="08" >August</option>
           <option value="09" >September</option>
           <option value="10" >October</option>
           <option value="11" >November</option>
           <option value="12" >December</option>
         </select>
		<input type="text" name="m_year" value="" size="4" maxlength="4" />
</form>
	  </tr>
      <tr>

[/HTML]

Edit ( Again ):

Then to recieve your data you need to do:

[PHP]
$mDay = $_POST['m_day'] said:**
> ;
$mYear = $_POST['m_year'];
[/PHP]


hahaah............THXXXXXXX 

i am really stupid ........^^""""

---

### Post by v8YKxgHe on 2006-06-20
=) All works then?

---

### Post by 008325 on 2006-06-20
[QUOTE=AlexC_]=) All works then?[/QUOTE]

yeah , really miss the $POST ^^"

thx a lot

---

### Post by v8YKxgHe on 2006-06-20
It's ok - glad to help, ( it's $_POST not $POST btw )

---

