---
title: "Problems with WebServer"
date: 2010-09-21
forum: Server Platforms
---

### Post by k33bz on 2010-09-21
For some reason I cant get this program to work on my webserver.

From the program I downloaded:
```
license:
this software (propertymanagement-software.org) is 100% free and may be used free of charge. you may not redistribute or sell this software.

installation:
-copy all files to your web host
-use phpmyadmin or your mysql interface to run site.sql against your database.
-open site.xml and edit the database section with your database details.
-go to index.php and login with username of admin with a password of test.
-be sure to change the passwords for the admin and regular user.

Setup the site.xml file with your database settings as follows.

<database type="mysql">
   <server>database server address</server>
   <login>database login</login>
   <password>database password</password>
   <default>mysql database name</default>
</database>

Add this to your htaccess file to prevent viewing of the xml config file:
<Files ~ ".xml"> Order allow,deny Deny from all Satisfy All </Files>

To use a different currency:
change [preffix="$"] in
forms\admin\expenses\add.xml (line 48 and 61)
forms\admin\expenses\details.xml (line 9 and 57)

To edit the year ranges edit line:
forms\admin\expenses\add.xml (line 58)
```

What I have done so far is installed mysql-server, phpmyadmin, copied all files into /var/www, created a table called property, imported site.sql (within phpmyadmin) and verified it was there(via cmd line mysql), edited site.xml
THIS IS AN EXAMPLE OF SITE.XML, THIS IS NOT MY PASSWORD:
```
        <database type="mysql">
   <server>192.168.1.4</server>
   <login>root</login>
   <password>test</password>
   <default>property</default>
</database>

```

however when I go to 192.168.1.4/index.php (server's local ip) I get nothing, it is blank. (Verified that apache is set up right with the default index.html) I can go to the other folders that are inside /var/www.
Not sure if there is a problem with file structures, the database, permissions, configs, or anything else, I am stuck. :(

---

### Post by Ryan Dwyer on 2010-09-21
I would try changing the MySQL server address in the XML to localhost or 127.0.0.1. Your MySQL service might not be listening on 192.168.1.4.

If that doesn't fix it, check your /var/log/apache2/error.log to see what the cause is.

---

### Post by k33bz on 2010-09-21
> **Ryan Dwyer said:**
> I would try changing the MySQL server address in the XML to localhost or 127.0.0.1. Your MySQL service might not be listening on 192.168.1.4.

If that doesn't fix it, check your /var/log/apache2/error.log to see what the cause is.

ok, tried that as localhost and 127.0.0.1 yet no luck, I am getting errors on apache2 log though, here is the print out:
```
keebler@FileServer:/var/www$ cat /var/log/apache2/error.log
[Mon Sep 20 20:08:55 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Mon Sep 20 20:08:58 2010] [notice] caught SIGTERM, shutting down
[Mon Sep 20 20:08:59 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Mon Sep 20 20:09:01 2010] [notice] Graceful restart requested, doing restart
[Mon Sep 20 20:09:01 2010] [notice] Apache/2.2.14 (Ubuntu) configured -- resuming normal operations
[Mon Sep 20 20:16:43 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Sep 20 20:16:43 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Mon Sep 20 20:19:44 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Sep 20 20:19:45 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Mon Sep 20 20:20:08 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Mon Sep 20 20:20:08 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Mon Sep 20 20:21:44 2010] [error] [client 192.168.1.102] File does not exist: /var/www/favicon.ico
[Mon Sep 20 20:21:47 2010] [error] [client 192.168.1.102] File does not exist: /var/www/favicon.ico
[Mon Sep 20 20:44:30 2010] [error] [client 192.168.1.102] PHP Warning:  require(config.php): failed to open stream: No such file or directory in /var/www/index.php on line 4
[Mon Sep 20 20:44:30 2010] [error] [client 192.168.1.102] PHP Fatal error:  require(): Failed opening required 'config.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php on line 4
[Mon Sep 20 20:45:21 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Mon Sep 20 20:47:02 2010] [error] [client 192.168.1.102] File does not exist: /var/www/var
[Mon Sep 20 21:19:50 2010] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/msql.so' - /usr/lib/php5/20090626+lfs/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Mon Sep 20 21:19:51 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Mon Sep 20 21:20:48 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 05:35:19 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 05:35:28 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 05:57:49 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:09:09 2010] [error] [client 192.168.1.102] script '/var/www/phpinfo.php' not found or unable to stat
[Tue Sep 21 06:11:09 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:11:16 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:13:12 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:18:21 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:22:23 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:22:26 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:24:23 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:28:54 2010] [error] [client 192.168.1.102] File does not exist: /var/www/var
[Tue Sep 21 06:29:03 2010] [error] [client 192.168.1.102] File does not exist: /var/www/var
[Tue Sep 21 06:29:15 2010] [error] [client 192.168.1.102] File does not exist: /var/www/www
[Tue Sep 21 06:29:20 2010] [error] [client 192.168.1.102] script '/var/www/templates/admin/login.php' not found or unable to stat
[Tue Sep 21 06:30:27 2010] [error] [client 192.168.1.102] File does not exist: /var/www/templates/admin/images, referer: http://192.168.1.4/templates/admin/login.htm
[Tue Sep 21 06:30:27 2010] [error] [client 192.168.1.102] File does not exist: /var/www/templates/admin/images, referer: http://192.168.1.4/templates/admin/login.htm
[Tue Sep 21 06:30:41 2010] [error] [client 192.168.1.102] script '/var/www/templates/admin/index.php' not found or unable to stat, referer: http://192.168.1.4/templates/admin/login.htm
[Tue Sep 21 06:31:03 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:39:52 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:39:55 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:39:57 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:42:46 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:48:26 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:48:59 2010] [error] [client 192.168.1.102] File does not exist: /var/www/home
[Tue Sep 21 06:49:57 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:50:05 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 06:53:49 2010] [error] [client 192.168.1.102] PHP Fatal error:  Class 'CXMLParser' not found in /var/www/lib/config.php on line 2, referer: http://192.168.1.4/lib/
[Tue Sep 21 06:53:58 2010] [error] [client 192.168.1.102] PHP Fatal error:  Class 'CLibrary' not found in /var/www/lib/forms.php on line 310, referer: http://192.168.1.4/lib/
[Tue Sep 21 06:56:14 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 07:08:45 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 07:21:37 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 07:47:18 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
[Tue Sep 21 07:47:25 2010] [error] [client 192.168.1.102] PHP Fatal error:  Cannot redeclare CSQLAdmin::$functions in /var/www/lib/sqladmin.php on line 31
keebler@FileServer:/var/www$ 

```

---

### Post by k33bz on 2010-09-21
CSQLAdmin

```
<?php



class CSQLAdmin extends CLibrary {



	/**

	* description

	*

	* @var type

	*

	* @access type

	*/

	var $form;



	/**

	* description

	*

	* @var type

	*

	* @access type

	*/

	var $functions;

	



	/**

	* description functions list which will be executed in variouse points of sqladmin

	*

	* @var type

	*

	* @access type

	*/

	var $functions;

	



	function CSQLAdmin($section , $templates , $db , $tables , $extra = "") {

		global $_CONF;



		if (!$_GET["page"])

			$_GET["page"] = 1;		





		parent::CLibrary("SQLAdmin");

		

		//checking if the templates are orblects or path to a template file

		if (!is_array($templates))					

			//if path the load the tempmate form that file

			$this->templates = array("generic_form" => new CTemplate($templates));

		else

			$this->templates = $templates;

		

		$this->db = $db;

		$this->tables = $tables;

		//extra variables to be passed to cform

		$this->extra = $extra;



		//loading the forms , changed the varialbes locations, but still keeping the compatibility

		$path = ($_CONF["forms"]["adminpath"] ? $_CONF["forms"]["adminpath"] : $_CONF["formspath"] );

		if (dirname($section)) {



			$path .= dirname($section) . "/" ;

			$section = basename($section);

		}

		

		//debuging part 

		if (defined("PB_DEBUG") && (PB_DEBUG == "1"))

			echo "<br>FILE:SQLADMIN:MAIN:{$path}{$section}.xml";



		$conf = new CConfig( $path . $section . ".xml");



		$this->forms = $conf->vars["form"];

		

		//loading the edit/add forms

		if (is_array($this->forms["forms"])) {

			foreach ($this->forms["forms"] as $key => $val) {	

				unset($conf);



				//debuging part 

//				if (defined("PB_DEBUG") && PB_DEBUG == "1")		

//					echo "<br>FILE:SQLADMIN:SECTION:{$path}{$section}.xml";



				$conf = new CConfig($path . $val );

				$this->forms["forms"][$key] = $conf->vars["form"];



				//adding the tables

				$this->forms["forms"][$key]["table"] = $this->forms["table"];

				$this->forms["forms"][$key]["table_uid"] = $this->forms["table_uid"];

				$this->forms["forms"][$key]["xmlfile"] = $path . $val ;

			}			

		}



		$this->form = new CForm($this->templates["generic_form"], &$db , &$tables);

	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function FormList($items = "") {

		global $base;



		//checking if hte values weren't inputed ion the main object

		if (is_array($this->items)) {

			$items = $this->items;

		}		



		//crap, preexecute a function, which is suposed in some times to preload the items too



		if (is_array($this->functions["list"]["pre"]))

			call_user_func($this->functions["list"]["pre"], &$items , &$items_count);



		//if i got no elements from preloader functions, then i load it manualy

		if (!is_array($items)) {



			//cheking if is a normal browse or a search method

			if (isset($this->forms["uridata"]["search"]) && ($_GET[$this->forms["uridata"]["action"]] == $this->forms["uridata"]["search"])) {



				$items = $this->db->QuerySelectLimit($this->tables[$this->forms["forms"]["list"]["table"]],"*", "`" . $_GET["what"] . "` " . ( $_GET["type"] == "int" ? "='" . $_GET["search"] . "'" : "LIKE '%" . $_GET["search"] . "%'"),(int) $_GET["page"],$this->forms["forms"]["list"]["items"]);

				$count = $this->db->RowCount($this->tables[$this->forms["forms"]["list"]["table"]] , " WHERE `" . $_GET["what"] . "` " . ( $_GET["type"] == "int" ? "='" . $_GET["search"] . "'" : "LIKE '%" . $_GET["search"] . "%'"));



			} else {

			

				$items = $this->db->QuerySelectLimit($this->tables[$this->forms["forms"]["list"]["table"]],"*","",(int) $_GET["page"],$this->forms["forms"]["list"]["items"]);

				$count = $this->db->RowCount($this->tables[$this->forms["forms"]["list"]["table"]]);

			}

		}



		$_GET["page"] = $_GET["page"] ? $_GET["page"] : 1;

		//auto index the element

		$start = $this->forms["forms"]["list"]["items"] * ($_GET["page"] - 1 );



		if (is_array($items)) {

			foreach ($items as $key => $val) {

				$items[$key]["_count"] = ++$start;

			}			

		}		



		//$data = new CForm($this->templates["generic_form"], &$this->db , &$this->tables);

		return $this->form->SimpleList($this->forms["forms"]["list"] , $items , $count , $this->extra["list"]);

	}





	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function SetFunction( $form , $event , $function) {

		$this->functions[$form][$event] = $function;

	}

	



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function ListProcess($pre = "" , $after = "" ) {



		$this->functions["list"]["pre"] = $pre;

		$this->functions["list"]["after"] = $after;

	}



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function StoreRecord($redirect = true) {

		global $base, $_CONF;



		//validating the input data

		if ($_SERVER["REQUEST_METHOD"] == "POST") {



			//doing a autodetect for storing type , edit or add

			//if $_GET["type"]	is set is simple, else detecting after the id form

			if (!isset($_GET["type"])) {

				if ($_POST[$this->forms["table_uid"]])

					$_GET["type"] = "edit";

				else

					$_GET["type"] = "add";

			}	



			//if validation succeeds then i move the files from /tmp to their directory, else i will proceed to add

			//precheck for uploaded files, like temporary images, etc.

			$form = $this->forms["forms"][$_GET["type"]];



			if (is_array($form["fields"])) {

				foreach ($form["fields"] as $key => $val) {



					switch ($val["type"]) {



						case "date":

							$_POST[$key] = mktime ( $_POST[$key . "_hour"] , $_POST[$key . "_minute"] , $_POST[$key . "_second"] , $_POST[$key. "_month"] , $_POST[$key. "_day"] , $_POST[$key. "_year"]);

						break;



						case "droplist":

							if ($val["subtype"] == "multiple") {



								//detect the fields which should be available for this field

								if (is_array($_POST)) {

									

									foreach ($_POST as $k => $v) {

										if (strstr($k , $key . "_option_")) {

											$option[] = $v;

										}										

									}						

									//ok, now build the result

									if (is_array($option)) {

										$_POST[$key] = implode($val["tree"]["db_separator"],$option);

									} else {

										$_POST[$key] = "";

									}

								} else {

									

								}

							}

							

						break;



						case "upload":

							$file = true;

						case "image":

							unset($_POST[$key]);



							//checking how choosed the client to set the image

							switch ($_POST[$key . "_radio_type"]) {

								case 0:

									//checking if the client specified any image type

									if (is_array($_FILES[$key . "_upload_client"]) && is_uploaded_file($_FILES[$key . "_upload_client"]["tmp_name"])) {									

										$img = &$_FILES[$key . "_upload_client"];

										//temporary upload the file in images/upload/tmp/

										$name = $_POST[$key . "_temp"] != "" ? $_POST[$key . "_temp"] : $val["file"]["default"] . time() . $val["file"]["ext"];	

										

										@move_uploaded_file($img["tmp_name"] , $_CONF["path"] . $_CONF["upload"] . "tmp/" . $name );



										// generate the tn image

										if ($val["tn"]["generate"] == "true") {

											$base->image->Resize(

																	$_CONF["path"] . $_CONF["upload"] . "tmp/" . $name ,

																	$_CONF["path"] . $_CONF["upload"] . "tmp/" . $val["tn"]["preffix"] . $name ,

																	$val["tn"]["width"]

																);

											$_POST["tn_" . $key] = "1";

										}

										

										//setting read/delete/save permission for all users, usefull if the httpd is working as normal user ( most cases )

										chmod ($_CONF["path"] . $_CONF["upload"] . "tmp/" . $name , 0777);

//										die;

										//setting the temp variable

										$_fields["values"][$key . "_temp"] = $name;

										$_POST[$key . "_temp"] = $name;

										$_POST[$key . "_file"] = $_FILES[$key . "_upload_client"]["name"];

										$_POST[$key] = "1";



									}								

								break;



								case "1":

									//, the guy wants to download a ing image



									if ($_POST[$key . "_upload_web"] != "http://") {										

										//i have to be very carefully here, if the image is not a valid link, then 

										//everithing get messed.

										$image = @GetFileContents($_POST[$key . "_upload_web"]);

										

										$name = $_POST[$key . "_temp"] != "" ? $_POST[$key . "_temp"] : $val["file"]["default"] . time() . $val["file"]["ext"];



										SaveFileContents( $_CONF["path"] . $_CONF["upload"] . "tmp/" . $name , $image);

										chmod ($_CONF["path"] . $_CONF["upload"] . "tmp/" . $name , 0777);



										// generate the tn image

										if ($val["tn"]["generate"] == "true") {

											@$base->image->Resize(

																	$_CONF["path"] . $_CONF["upload"] . "tmp/" . $name ,

																	$_CONF["path"] . $_CONF["upload"] . "tmp/" . $val["tn"]["preffix"] . $name ,

																	$val["tn"]["width"]

																);



											$_POST["tn_" . $key] = "1";

										}



										//setting the temp variable

										$_fields["values"][$key . "_temp"] = $name;

										$_POST[$key . "_temp"] = $name;

										$_POST[$key . "_file"] = basename($_POST[$key . "_upload_web"]);

										$_POST[$key] = "1";

									}



								break;



								case "-1":

//									echo "<pre style=\"background-color:white\">";

//									print_r($_POST);

//									die;

									//trying to remove the tmp image is exists

									if (file_exists($_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"]) && is_file($_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"]))

										@unlink($_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"]);										

									//removing the original image too if exists

									else

										@unlink($_CONF["path"] . $_CONF["upload"] . $val["path"] . $val["file"]["default"] . $_POST[$val["file"]["field"]] . $val["file"]["ext"]);



									$_fields["values"][$key . "_radio_type"] = 0;



									$_POST[$key] = 0;

									$_fields["values"][$key . "_temp"] = "";

									$_POST[$key . "_temp"] = "";

									$_POST[$key . "_file"] = "";

								break;



							}

							//hm ... checking if that IS A REAL IMAGE

							if ($_POST[$key . "_temp"] && !$file) {

								

								$img = @GetImageSize($_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"]);



								if (!is_array($img)) {



									//removing the image, maybe in future return the er a proper answer

									//echo "MOHHHHH";

									@unlink($_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"]);

									$_POST[$key . "_temp"] = "";

									$_POST[$key] = 0;

								}									

							}

																

						break;

					}							

				}						

			}



			//force for no validation sometimes

			if ($_GET["FORMvalidate"] == "false")

				$fields = "";

			else

				$fields = $this->form->Validate($this->forms["forms"][$_GET["type"]] , $_POST);

			

			if (!is_array($fields)) {

				//adding to database

				

				if (!$_POST[$this->forms["forms"]["add"]["table_uid"]]) {



					$id = $this->db->QueryInsert($this->tables[$this->forms["forms"]["add"]["table"]] , $_POST);

					$_POST[$this->forms["forms"]["add"]["table_uid"]] = $id;

				

				} else {

					$this->db->QueryUpdate($this->tables[$this->forms["forms"]["edit"]["table"]] , $_POST , "`" . $this->forms["forms"]["edit"]["table_uid"] . "`='" . $_POST[$this->forms["forms"]["edit"]["table_uid"]] . "'" );



					$id = $_POST[$this->forms["forms"]["edit"]["table_uid"]];

				}



				//data stored, taking care of uploade files/images, etc

				if (is_array($form["fields"])) {

					foreach ($form["fields"] as $key => $val) {



						switch ($val["type"]) {

							case "upload":

							case "image":



							//checking if is really e file, else if no tmp is set then it can be the folder where are stored the values

								if (is_file($_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"])) {



									//moving the image stored in temp variable

									//check if the file already exists

									if (is_file($_CONF["path"] . $_CONF["upload"] . $val["path"] . $val["file"]["default"] . $_POST[$val["file"]["field"]] . $val["file"]["ext"])) {

										@unlink($_CONF["path"] . $_CONF["upload"] . $val["path"] . $val["file"]["default"] . $_POST[$val["file"]["field"]] . $val["file"]["ext"]);

									}

									

									@rename(

										$_CONF["path"] . $_CONF["upload"] . "tmp/" . $_POST[$key . "_temp"] ,

										$_CONF["path"] . $_CONF["upload"] . $val["path"] . $val["file"]["default"] . $_POST[$val["file"]["field"]] . $val["file"]["ext"]

										);	



										// generate the tn image

										if ($val["tn"]["generate"] == "true") {

											@rename(

												$_CONF["path"] . $_CONF["upload"] . "tmp/" . $val["tn"]["preffix"] . $_POST[$key . "_temp"] ,

												$_CONF["path"] . $_CONF["upload"] . $val["path"] . $val["tn"]["preffix"] . $val["file"]["default"] . $_POST[$val["file"]["field"]] . $val["file"]["ext"]

												);	



										}



									//setting the image as true

									$_POST[$key] = 1;

									//updateing the database

									$this->db->QueryUpdate($this->tables[$this->forms["forms"]["edit"]["table"]] , $_POST , "`" . $this->forms["forms"]["edit"]["table_uid"] . "`='" . $_POST[$this->forms["forms"]["edit"]["table_uid"]] . "'" );

								} 

							break;



							default:

								if (is_array($val["file"]))

									SaveFileContents($_CONF["path"] . $_CONF["upload"] . $val["file"]["path"] . $val["file"]["default"] . $_POST[$val["file"]["field"]] . $val["file"]["ext"] , $_POST[$key] );

							break;



						}

					}

				}



				if (!$_GET["type"]) {

					$_GET["type"] = $_POST[$this->forms["forms"]["table_uid"]] ? "edit" : "add";

				}

				



				$this->templates["generic_form"]->blocks["Temp"]->input = $this->forms["forms"][$_GET["type"]]["redirect"];

				//replacing the values

				//die($this->templates["generic_form"]->blocks["Temp"]->Replace($_POST));



				if ($_GET["returnURL"]) {

					header("Location:" . urldecode($_GET["returnURL"]));

					exit;

				}

				

				if ($redirect == true) {

					header("Location: " . CryptLink($this->templates["generic_form"]->blocks["Temp"]->Replace(array_merge($_GET,$_POST))));

					exit;

				} else {

					return true;

				}

			}

								

		} else {

			die("ARGH!!!");

			//redirecting to list page

			header("Location:" . str_replace("&action=store" , "" , $_SERVER["REQUEST_URI"]));

			exit;

		}				





		if (is_array($_fields["values"]))

			$fields["values"] = array_merge($fields["values"], $_fields["values"]);

		

		return $this->form->Show($this->forms["forms"][$_GET["type"]] , $fields);				

	}

	

	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function RestoreURI($section) {

		if (is_array($_GET)) {

			foreach ($_GET as $key => $val) {

				$out[$key] = $key . "=" . $val;

			}

						

			$out[$this->forms["uridata"]["action"]] = $this->forms["uridata"]["action"] . "=" . $this->forms["uridata"][$section];

			unset($out[$this->forms["table_uid"]]);



			return CryptLink($_SERVER["SCRIPT_NAME"] . "?" . implode("&" , $out));



			//return $_

		}		

	}

	



	/**

	* description

	*

	* @param

	*

	* @return

	*

	* @access

	*/

	function DoEvents($section = ""  , $extra = "" , $values = "") {

		global $base , $_CONF;



		if (is_array($extra)) {

			$this->extra = array_merge($this->extra , $extra);

		}

		

		switch ($_GET[$this->forms["uridata"]["action"]]) {



			case $this->forms["uridata"]["delete"]:

	



				if (($_GET["rconfirm"] == "true")&&($_GET["confirmed"] != "true")) {

					return $this->templates["generic_form"]->blocks["DeleteItem"]->Replace(array(

									"title" => $_GET["title"] ? urldecode($_GET["title"]) : "Delete Item",

									"description" => $_GET["description"] ? urldecode($_GET["description"]) : "Are you sure you want to delete this record?",

									"return" => urldecode($_GET["returnURL"]),

									"cancel_location" => urldecode($_GET["returnURL"]),

									"delete_location" => $_SERVER["REQUEST_URI"] . "&confirmed=true"

								));

				}



				

				//searching for element

				$data = $this->db->QFetchArray("SELECT * FROM `" . $this->tables[$this->forms["forms"]["edit"]["table"]] . "` WHERE `" . $this->forms["forms"]["edit"]["table_uid"] . "`='" . $_GET[$this->forms["forms"]["edit"]["table_uid"]] . "'" );



				//checking if this is a valid data

				if (is_array($data)) {

					$this->db->Query("DELETE FROM `" . $this->tables[$this->forms["forms"]["edit"]["table"]] . "` WHERE `" . $this->forms["forms"]["edit"]["table_uid"] . "`='" . $_GET[$this->forms["forms"]["edit"]["table_uid"]] . "'" );

				}

			

				if ($_GET["returnURL"]) {

					header("Location: " . CryptLink(urldecode($_GET["returnURL"])));

					exit;

				} else {

					header("Location:" . $_SERVER["HTTP_REFERER"]/*$this->RestoreURI("list")*/);

					exit;

				}

				

			break;



			case $this->forms["uridata"]["store"]:

				return $this->StoreRecord();

			break;



			case $this->forms["uridata"]["add"]:

				$fields["values"] = $values;

				return $this->form->Show($this->forms["forms"]["add"] , $fields , $this->extra["add"]);

			break;



			case $this->forms["uridata"]["edit"]:

				//searching for element

				$data = $values["edit"] ? $values["edit"] : $this->db->QFetchArray("SELECT * FROM `" . $this->tables[$this->forms["forms"]["edit"]["table"]] . "` WHERE `" . $this->forms["forms"]["edit"]["table_uid"] . "`='" . $_GET[$this->forms["forms"]["edit"]["table_uid"]] . "'" );



				//checking if this is a valid data

				if (is_array($data)) {

					$fields["values"] = $data;

					return $this->form->Show($this->forms["forms"]["edit"] , $fields , $this->extra["edit"]);

				} 



				header("Location:" . $this->RestoreURI("list"));

				exit;

				

			break;



			case $this->forms["uridata"]["details"]:

				//searching for element

				$data = $this->db->QFetchArray("SELECT * FROM `" . $this->tables[$this->forms["forms"]["edit"]["table"]] . "` WHERE `" . $this->forms["forms"]["edit"]["table_uid"] . "`='" . $_GET[$this->forms["forms"]["edit"]["table_uid"]] . "'" );



				//checking if this is a valid data

				if (is_array($data)) {

					$fields["values"] = $data;

					return $this->form->Show($this->forms["forms"]["details"] , $fields, $this->extra["details"]);

				} 



				header("Location:" . $this->RestoreURI("list"));

				exit;

				

			break;



			case $this->forms["uridata"]["search"]:

			case $this->forms["uridata"]["list"]:

			default:

				

				return $this->FormList($values["list"]);

			break;



		}	

	}

}



?>
```

---

### Post by Ryan Dwyer on 2010-09-21
Did you make edits to that CSQLAdmin file? Remove one of the "var $functions;" and try again.

---

### Post by k33bz on 2010-09-21
> **Ryan Dwyer said:**
> Did you make edits to that CSQLAdmin file? Remove one of the "var $functions;" and try again.

Ya I had just did that, still getting the same results with index.php, blank pages. 


I am also seeing this through phpmyadmin
```

The additional features for working with linked tables have been deactivated. To find out why click here.
```
going there I have this
```
$cfg['Servers'][$i]['tracking'] ... 	not OK [ Documentation ]
Tracking: Disabled
```

all others are enabled. Not sure if that has anything to do with it or not. And cant figure out how to enable it.

---

### Post by k33bz on 2010-09-21
```
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/msql.so' - /usr/lib/php5/20090626+lfs/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Tue Sep 21 09:10:26 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined index: NAME in /var/www/lib/config.php on line 107
[Tue Sep 21 09:11:18 2010] [error] [client 192.168.1.102] PHP Notice:  Undefined variable: type in /var/www/lib/database.php on line 66
```




Not sure if anyone wants me to show a printout of database.php or config.php

/lib/congif.php  LINE 107 = ```
if ($this->attr["NAME"] != "")
```
```
<?php

class CConfig extends CXMLParser {

	/**

	* current depth in xml tree

	*

	* @var int

	*

	* @access private

	*/

	var $depth = 0;



	/**

	* depth tags parser helper

	*

	* @var array

	*

	* @access private

	*/

	var $tags = array();



	/**

	* config tree

	*

	* @var array

	*

	* @access public

	*/

	var $vars = array();



	/**

	* creates the xml parser and optionally loads a config file

	*

	* @param string $file_name	config file name to load

	*

	* @return void

	*

	* @access public

	*/

	function CConfig($file_name = "") {

		parent::CXMLParser();



		if ($file_name != "")

			$this->Load($file_name);

	}



	/**

	* xml parser open tag handler

	*

	* @param object $parser	actual expat parser

	* @param string $tag	current xml tag

	* @param array $attr	current tag attributes

	*

	* @return void

	*

	* @acces private

	*/

	function HNDTagOpen($parser,$tag,$attr) {//echo "<pre>";

		// call parent to save tag and attr info for cdata handler

		parent::HNDTagOpen($parser,$tag,$attr);

		

		// expand helper tag array

		$this->tags[$this->depth] = $tag;

		$this->depth++;



		// prepare dynamic code for attr handling

		foreach ($this->tags as $key => $val)

			$code[] = "\"" . strtolower($val) . "\"";



		// build code

		$node = implode("][",$code);

		$code = "foreach (\$attr as \$key => \$val) if (\$key != \"NAME\") \$this->vars[$node][strtolower(\$key)] = \"\$val\"; else \$this->vars[\$attr[\"NAME\"]][strtolower(\"\$key\")] = \"\$val\";";



		// and finally execute

		eval($code);

	}



	/**

	* close tag handler

	*

	* @param object $parser	actual expat parser

	* @param string $tag	current xml tag

	*

	* @return void

	*

	* @access private

	*/

	function HNDTagClose($parser,$tag) {

		// compress helper tag array

		unset($this->tags[$this->depth]);

		$this->depth--;

	}



	/**

	* character data handler

	*

	* @param object $parser	actual expat parser

	* @param string $cdata	current tag character data

	*

	* @return void

	*

	* @access private

	*/

	function HNDCData($parser,$cdata) {

		$cdata = str_replace("[amp]","&",$cdata);

		//echo "<br>" . $cdata;

		// create the proper tree node if NAME attribute is set

		if ($this->attr["NAME"] != "")

			$this->tags[count($this->tags) - 1] = $this->attr["NAME"];



		// cleanup cdata

		$cdata = trim($cdata);

		//$cdata = preg_replace("/(\015\012)|(\015)|(\012)/","",$cdata);



		// only parse if cdata not void

		if ($cdata != "") {

			//print_r($this->attr);

			//echo "<br>" . $cdata;



			// prepare dynamic code

			foreach ($this->tags as $key => $val)

				$code[] = "\"" . strtolower($val) . "\"";



			// build code

			$code = "\$this->vars[" . implode("][",$code) . "] = \"" . $cdata . "\";";



			// and finally execute

			eval($code);

		}

	}



	/**

	* load the config file and parse it

	*

	* @param string $file_name	config filename to load

	*

	* @return void

	*

	* @acces public

	*/

	function Load($file_name) {

		parent::Parse($this->data = str_replace("&","[amp]",GetFileContents($file_name)));

		$this->vars = ArrayReplace("[amp]" , "&" , $this->vars );

	}

}

?>
```



lib/database.php  LINE 66 = ```
 $this->type = $type;
```
```
<?php

// return types

define("DB_RT_ARRAY",0);  // return row as an assoc aray where fieldnames are keys

define("DB_RT_OBJECT",1);  // return row as an object where fieldnames are properties



class CDatabase{

 /**

 * database type

 *

 * @var string

 *

 * @access private

 */

 var $type;



 /**

 * database connection id

 *

 * @var resource

 *

 * @access private

 */

 var $conn_id;



 /**

 * name of the current selected database

 *

 * @var string

 *

 * @access private

 */

 var $current_db;



 /**

 * number of queries per session

 *

 * @var int

 *

 * @access private

 */

 var $num_queries;



 /**

 * specifies if there were any modifications to the database [write queries]

 *

 * @var bool

 *

 * @access private

 */

 var $modif = FALSE;



 /**

 * initializes module and connects to the database

 *

 * @param array $connect_params connection parameters

 *

 * @return void

 *

 * @acces public

 *

 * @see Connect

 */

 function CDatabase($connect_params = "") {

  $this->name = "database";



  $this->type = $type;



  if ($connect_params != "")

   $this->Connect($connect_params);

 }



 /**

 * connects to the database

 *

 * @param array $connect_params connection parameters

 *

 * @return void

 *

 * @access public

 */

 function Connect($connect_params = "") {

  extract($connect_params);

  //resource mysql_connect ( [string server [, string username [, string password [, bool new_link !!! [, int client_flags ]]]]] )

  $this->conn_id = mysql_connect($server,$login,$password,TRUE) or die("CDatabase::Connect() error " . mysql_error($this->conn_id));



  if ($default != "")

   $this->SelectDB($default);

 }



 /**

 * closes the database connection

 *

 * @return void

 *

 * @access public

 */

 function Close() {

  mysql_close($this->conn_id);

 } 

 

 /**

 * selects and sets the current database

 *

 * @param string $database

 *

 * @return void

 *

 * @access public

 */

 function SelectDB($database) {

  mysql_select_db($database,$this->conn_id) or die("CDatabase::SelectDB() error");

  $this->current_db = $database;

 }

 

 /**

 * queries the database

 *

 * @param string $query actual sql query

 *

 * @return resource or NULL

 *

 * @access public

 */

 function Query($query,$db = "") {//debug($query);

  $this->num_queries++;

  //$this->SelectDB($this->current_db);

  //echo "<br>$query";  

  if ($db)

   $result = mysql_db_query($db ,$query,$this->conn_id);// or die(mysql_error());

  else

   $result = mysql_query($query,$this->conn_id) or die($query . mysql_error());



  if (in_array(substr($query,0,strpos($query," ")),array("INSERT", "UPDATE", "DELETE")))

   $this->modif = TRUE;



  return $result;

 }



 function FetchObject($result) {

  return mysql_fetch_object($result);

 }



 function FetchRow($result) {

  return mysql_fetch_row($result);

 }



 function FetchArray($result,$result_type = MYSQL_ASSOC) {

  return mysql_fetch_array($result,$result_type);

 }



 function NumRows($result) {

  return mysql_num_rows($result);

 }



 function AffectedRows() {

  return mysql_affected_rows($this->conn_id);

 }



 function InsertID() {

  return mysql_insert_id($this->conn_id);

 }



 function NumQueries() {

  return $this->num_queries;

 }



 function QFetchObject($query) {

  return $this->FetchObject($this->Query($query));

 }



 function QFetchRow($query) {

  return $this->FetchRow($this->Query($query));

 }



 function QFetchArray($query) {

  return $this->FetchArray($this->Query($query));

 }



 /**

 * returns the number of rows from a table based on a certain [optional]

 * where clause

 *

 * @param string $table   table in which to count rows

 * @param string $where_clause optional where clause [see sql WHERE clause]

 *

 * @return int row count

 *

 * @access public

 */

 function RowCount($table,$where_clause = "") {

  $result = $this->FetchRow($this->Query("SELECT COUNT(*) FROM `$table` $where_clause;"));

  return $result[0];

 }



 /**

 * fetch an array w/ rows from the database

 *

 * @param resource $result sql query result

 * @param int $return_type row return type [can be DB_RT_ARRAY or DB_RT_OBJECT]

 * @param string $key  key the returned array by a certain row field [defaults to ""]

 *

 * @return array with rows or NULL if none fetched

 *

 * @access public

 */

 function FetchRowArray($result,$return_type = DB_RT_ARRAY,$key = "") {

  $ret_val = array();

  $i = 0;



  // dont panic. its just ternary operators in action :]

  while ($row = (($return_type == DB_RT_ARRAY) ? $this->FetchArray($result) : $this->FetchObject($result)))

   $ret_val[(($key == "") ? $i++ : (($return_type == DB_RT_ARRAY) ? $row["$key"] : $row->$key))] = $row;



  // see if any rows were fetched and return accordingly

  return (count($ret_val) != 0) ? $ret_val : NULL;

 }



 /**

 * FetchRowArray wrapper

 *

 * @param string $query sql query to send to FetchRowArray

 * @param int $return_type

 * @param string $key

 *

 * @return array

 *

 * @access public

 *

 * @see CDatabase::FetchRowArray

 */

 function QFetchRowArray($query,$return_type = DB_RT_ARRAY,$key = "") {

  return $this->FetchRowArray($this->Query($query),$return_type,$key);

 }



 /**

 * returns an array w/ the tables fields

 *

 * @param $table database table from which to get rows

 *

 * @return array

 *

 * @access public

 */

 function GetTableFields($table) {

  $fields = $this->QFetchRowArray("SHOW FIELDS FROM `$table`");

  $ret_val = array();



  foreach ($fields as $field)

   $ret_val[] = $field["Field"];



  return $ret_val;

 }



 /**

 * fetches a row from a table based on a certain id using the SELECT SQL query

 *

 * @param string $table  table in which to perform select

 * @param int $id   row id to fetch

 * @param string $fields  comma separated list of row fields to fetch [defaults to `*' all]

 * @param int $return_type row return type DB_RT_ARRAY|DB_RT_OBJECT [defaults to DB_RT_ARRAY]

 *

 * @return array w/ the fetched data or NULL if id not found

 *

 * @access public

 */

 function QuerySelectByID($table,$id,$fields = "*",$return_type = DB_RT_ARRAY) {

  // build query

  $query = "SELECT $fields FROM `$table` WHERE `id` = '$id'";



  // fetch row

  return ($return_type == DB_RT_ARRAY) ? $this->QFetchArray($query) : $this->QFetchObject($query);

 }



 /**

 * complex fetch row array w/ WHERE/LIMIT/ORDER SQL clauses and page modifier

 *

 * @param string $table   table to fetch rows from

 * @param string $fields   comma separated list of row fields to fetch

 * @param string $where_clause SQL WHERE clause [use empty to ignore]

 * @param int $start    limit start

 * @param int $count    number of rows to fetch

 * @param bool $pm    page modifier. if set to TRUE [default] $start becomes the page

 * @param string $order_by  field[s] to order the result by [defaults to void]

 * @param string $order_dir  order direction. can be ASC or DESC [defaults to ASC]

 * @param int $return_type  row return type [DB_RT_ARRAY(default)|DB_RT_OBJECT]

 *

 * @return array w/ fetched rows or NULL

 *

 * @access public

 */

 function QuerySelectLimit($table,$fields,$where_clause,$start,$count,$pm = TRUE,$order_by = "",$order_dir = "ASC",$return_type = DB_RT_ARRAY) {

  // check if $count is empty just to be safe

  $count = ($count == "") ? 0 : $count;



  // recompute $start if page modifier set

  $_start = ($pm == TRUE) ? ((($start == 0) ? 1 : $start) * $count - $count) : $start;



  // setup order clause

  $order_clause = ($order_by != "") ? "ORDER BY $order_by " . (in_array($order_dir,array("ASC","DESC")) ? "$order_dir " : "") : "";



  // setup where clause

  $where_clause = ($where_clause != "") ? "WHERE $where_clause " : "";



  // limit clause

  $limit_clause = ($start >= 0) ? "LIMIT $_start,$count" : "";

  

  // build query

  $query = "SELECT $fields FROM `$table` {$where_clause}{$order_clause}{$limit_clause}";



  // fetch rows

  return $this->QFetchRowArray($query,$return_type);

 }



 /**

 * builds and performes a SQL INSERT query based on the user data

 *

 * @param string $table table in which to perform insert

 * @param array $fields associative array w/ the row fields to be inserted

 *

 * @return void

 *

 * @access public

 */

 function QueryInsert($table,$fields) {

  // first get the tables fields

  $table_fields = $this->GetTableFields($table);



  if (count($fields) == 0) {

   $names[] = "id";

   $values[] = "''";

  } else

   // prepare field names and values

   foreach ($fields as $field => $value)

    // check for valid fields

    if (in_array($field,$table_fields)) {

     $names[] = "`$field`";

     $values[] = is_numeric($value) ? $value : "'" . addslashes($value) . "'";

    }



  // build field names and values

  $names = implode(",",$names);

  $values = implode(",",$values);



  // perform query

  $this->Query("INSERT INTO `$table` ($names) VALUES($values)");



  return $this->InsertID();

 }



 /**

 * builds and performs a SQL UPDATE query based on the user data

 *

 * @param string $table   table in which to perform update

 * @param array $fields   associative array w/ the fields to be updated

 * @param string $where_clause update where clause [see SQL WHERE clause]

 *

 * @return void

 *

 * @access public

 */

 function QueryUpdate($table,$fields,$where_clause) {

  if (is_array($fields)) {

   // first get the tables fields

   $table_fields = $this->GetTableFields($table);



   // prepare query

   foreach ($fields as $field => $value)

    // check for valid fields

    if (in_array($field,$table_fields))

     $pairs[] = "`$field` = " . (is_numeric($value) ? $value : "'" . addslashes($value) . "'");

//     $values[] = ;



   // build and perform query

   if (is_array($pairs))   

    $this->Query("UPDATE `$table` SET " . implode(", ",$pairs) . " WHERE($where_clause)");

  }

 }



 /**

 * builds and performs a SQL UPDATE query based on the user data

 *

 * @param string $table table in which to perform update

 * @param array $fields associative array w/ the fields to be updated

 *

 * @return void

 *

 * @access public

 */

 function QueryUpdateByID($table,$fields) {

  $id = $fields["id"];

  unset($fields["id"]);



  $this->QueryUpdate($table,$fields,"`id` = '$id'");

 }

}

?>


```



also I went back to the website I got this from (no documentation to start with) I noticed that it was last written on 7/12/06. Could I be having problems because it is not compatible with php5? And would need php4? Or maybe something else on the same lines?

---

### Post by k33bz on 2010-09-21
Bump

---

### Post by windependence on 2010-09-21
Near as I can tell you haven't done this. You only said you imported it. You need to RUN it from within phpMyAdmin.
 
-use phpmyadmin or your mysql interface to run site.sql against your database.
 
 
-Tim

---

### Post by k33bz on 2010-09-21
> **windependence said:**
> Near as I can tell you haven't done this. You only said you imported it. You need to RUN it from within phpMyAdmin.
 
-use phpmyadmin or your mysql interface to run site.sql against your database.
 
 
-Tim

Thought it meant the same thing, all the tables show up within phpmyadmin under DB property. So my bad, how do I run it then?

---

### Post by Ryan Dwyer on 2010-09-21
I have no idea why windependence instructed you to do that. Your database is already set up correctly.

If I were you I'd give up on their code as it obviously doesn't work. It doesn't matter what version of PHP you're using. If they didn't test and find a fatal error when loading the homepage then I'm sure it's probably riddled with exploits too.

---

### Post by k33bz on 2010-09-21
ya, I already gave up on it, looking for a different Property Management Software as we type. Just seems to be harder than I remember to find some. I will probable work on this one in my spare time till I get it all figured out. But I need something now, which is why I am looking around.

---

### Post by k33bz on 2010-09-21
I gave up on looking for different scripts to use. So I am back at the one that is making problems. Good news is I cleared up all the errors, except for one. And it is not the most important one to me as of yet.

The problem I am having is that pages are not loading up. Login page loads up, users page loads up. 

These are the pages that dont load up:

Details of user
add user
expenses list
details of expenses
add expenses
edit expenses
property list
add property
details of property
edit property

Can some one please help me with this, I will be more than happy to send you all the codes. Or something else can work out.

---

### Post by siggimagg on 2012-03-14
Hi - old post :)

Did you ever resolve this ?

Can you send me the fixes you made so far ?

br, Siggi

---

