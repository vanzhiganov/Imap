# Imap

PHP Wrapper class for frequently used php-imap functions.

# how to use

Connect to IMAP server

```
$imap_server = 'imap.yandex.ru';
$imap_user = 'chupakabra48';
$imap_password = 'MySuperP@ssw0rd';
$imap_port = 993;
$imap_ssl = true;
$imap_folder = "INBOX";

$t = new Imap($imap_server, $imap_user, $imap_password, $imap_port, $imap_ssl, $imap_folder);
```

Returns an Associative Array containing the number of recent, unread, and total messages

`$t->getInboxInformation()`

Returns an Associative Array containing the subject of every email along with the Message Id of each individual email.

`$t->getMessageIds());`

Given a new $host, $user, $pass, $port, $ssl, $folder inputs, this function will disconnect from the old connection and open a new connection to a specified server.

For the sake of the example, I am using the same information.

`$t->changeLoginInfo($host, $user, $pass, $port, $ssl, $folder);`

Returns an Associative Array containing detailed information about a specific Message Id.

`$t->getDetailedMessageInfo(2));`

Parses a given Email address and returns an Array containing the mailbox, host, and name of the given email address.

```
$a = $t->getDetailedMessageInfo(2);
$t->parseAddresses($a["reply"]));
```

Generate an email address to comply with RFC822 specifications.

```
$u = "testusername";
$h = "samplehost.com";
$n = "TestFirst TestLastName";
echo $t->createAddress($u, $h, $n);
```

Deletes a message matching the given Message Id.

`$t->deleteMessage(2);`

Returns an Array containing structural information about a given Message Id.

@see imap_fetchstructure (http://www.php.net/manual/en/function.imap-fetchstructure.php)

`print_r($t->getStructure(2));`

Returns the body type of a given Message Id.

`echo $t->getBodyType(2);`

Returns the encoding type of a given Message Id.

`echo $t->getEncodingType(2);`

Given an encoded Base64 message, returns the decoded text.

Encoded string reads: "Testing One Two Three"

`echo $t->decodeBase64("VGVzdGluZyBPbmUgVHdvIFRocmVl");`

Given a new folder, will disconnect and reconnect to the specified folder name.

`$t->changeFolder("NEW_FOLDER_NAME");`

Disconnects an active imap connection

`$t->disconnect();`
