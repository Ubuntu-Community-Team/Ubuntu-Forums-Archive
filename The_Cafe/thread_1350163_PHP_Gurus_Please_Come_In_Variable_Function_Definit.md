---
title: "PHP Gurus Please Come In: Variable Function Definition?"
date: 2009-12-09
forum: The Cafe
---

### Post by Gias Kay on 2009-12-09
Hi gurus *lol*

I have three function definitions here:

[PHP]function int_register() {
	$num_args = func_num_args();
	for ($i = 0; $i < $num_args; $i ++) {
		$parameter = func_get_arg($i);
		if (isset($_REQUEST[$parameter])) {
			global $$parameter;
			$$parameter = intval($_REQUEST[$parameter]);
		}
	}
}

function string_register() {
	$num_args = func_num_args();
	for ($i = 0; $i < $num_args; $i ++) {
		$parameter = func_get_arg($i);
		if (isset($_REQUEST[$parameter])) {
			global $$parameter;
			$$parameter = trim(escape_string(htmlentities($_REQUEST[$parameter])));
		}
	}
}

function array_register() {
	$num_args = func_num_args();
	for ($i = 0; $i < $num_args; $i ++) {
		$array = func_get_arg($i);
		if (isset($_REQUEST[$array])) {
			$process = "";
			foreach ($_REQUEST[$array] as $rip) {
				$process[] = trim(escape_string(htmlentities($rip)));
			}
			global $$array;
			$$array = array();
			foreach ($process as $parameter) {
				array_push($$array, $parameter);
			}
		}
	}
}[/PHP]

As you can see, there are lots of similar parts inside the definitions of these three functions; as such I am trying to find a way to compress them into one code bloc.

I've tried the variable function concept but it didn't work:

[PHP]$lolz = array('int_register', 'string_register', 'array_register');
foreach ($lolz as $lol) {
	function $lol() {
		[DEFINITIONS]
	}
}[/PHP]

I know it would be way lot easier if I redo the functions into something like:
[PHP]function register($flag) {
	switch ($flag) {
		case "int":
			[DEFINITION]
	}
}[/PHP]
But I regard this as a last resort and would not do so if there are other solutions. So... is there really any other solution?

---

### Post by Gias Kay on 2009-12-09
*bump*

---

