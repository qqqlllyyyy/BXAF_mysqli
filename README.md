# BXAF_mysqli
Safe and convenient way to handle SQL queries utilizing type-hinted placeholders.


Modified from SafeMySQL as following:
@author col.shrapnel@gmail.com
@link http://phpfaq.ru/safemysql


Key features
- set of helper functions to get the desired result right out of query, like in PEAR::DB
- conditional query building using parse() method to build queries of whatever comlexity, 
  while keeping extra safety of placeholders
- type-hinted placeholders


Type-hinted placeholders are great because 
- safe, as any other [properly implemented] placeholders
- no need for manual escaping or binding, makes the code extra DRY
- allows support for non-standard types such as identifier or array, which saves A LOT of pain in the back.


Supported placeholders at the moment are:

- ?s ("string")  - strings (also DATE, FLOAT and DECIMAL)
- ?i ("integer") - the name says it all 
- ?n ("name")    - identifiers (table and field names) 
- ?a ("array")   - complex placeholder for IN() operator  (substituted with string of 'a','b','c' format, without parentesis)
- ?u ("update")  - complex placeholder for SET operator (substituted with string of `field`='value',`field`='value' format)
and
- ?p ("parsed") - special type placeholder, for inserting already parsed statements without any processing, to avoid double - parsing.


Connection:

$db = new bxaf_mysqli(); // with default settings

$opts = array(
	'user'    => 'user',
	'pass'    => 'pass',
	'db'      => 'db'
);

$db = new bxaf_mysqli($opts); // with some of the default settings overwritten


Alternatively, you can just pass an existing mysqli instance that will be used to run queries 
instead of creating a new connection.
Excellent choice for migration!
