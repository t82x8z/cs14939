java c
Operating Systems and Systems Programming
Semester 1, 2024
Exercise 1
Deadline:  14 November, 4pm
The Task
Write a set of programs which maintains the ﬁrewall conﬁguation.1.  One program is aserver program.  Once started, the server should run for- ever. It waits for requests, process them and produce a speciﬁc response.The server maintains a collection of ﬁrewall rules.  For each rule in the collection of rules, the server also maintains a list of pairs of IP addresses and ports which have been queried and found to match this rule.   The server also maintains a list of all requests submitted to it.   The server program  should  accept  and  process  requests  and  return  a  response  as follows:
● Listing all requests in the order they were given.  The command for this request is R
● Adding a rule to the stored rules. This request expects a string which contains a ﬁrewall rule as speciﬁed below.  If the rule is valid, the rule is added the set of ﬁrewall rules.  The response is Rule  added if the rule has been added, and Invalid  rule if the string is not a valid rule. The command for this request is
A  
● Checking whether a given IP address and port are allowed according to the rules.  If this is the case, the IP address and port are added to list of matched queries for this rule.  If the given address and port are allowed according to several rules, you should add the IP address and port to only one rule.  If the given IP address and port is checked again, they may be added to a diferent rule.  If the input does not provide a valid IP address and a valid port, the response should be Illegal  IP  address  or  port  specified.   If the IP address and port  are valid  and should be  accepted  according to the rules,  the response should be  Connection  accepted.   If the IP  address  and port  are  valid  and  should  be  rejected  according  to  the  rules,  the response should be Connection  rejected.  The command for this request is
C    
● Delete a valid rule from the stored rules.  This should also delete the list of IP addresses and ports stored for this rule.  The rule should only  be  deleted  if the  server  stores  exactly  the  same  rule.   In  all other cases, no action should be taken except returning a suitable message. If the speciﬁcation of the rule is invalid, the response should be Rule  invalid.   If the rule is successfully deleted, the response should be Rule  deleted.  If the rule is valid but not found on the server, the response should be Rule  not  found.  The command for this request is
D  
● Return  all  rules  and  for  each  rule  list  all  IP  addresses  and  ports which are stored with it.  More precisely, for each rule, the response should be
Rule:  
where  is the speciﬁcation of the rule as given below, followed by
Query:    
for each query stored with this ﬁrewall rule.  The comma代 写Operating Systems and Systems Programming Semester 1, 2024 Exercise 1Haskell
代做程序编程语言nd for this request is L
● For any other request, the response should be Illegal  request. There are two ways of interacting with the server program.
● The ﬁrst one is to start the server with
-iwhere  is the way to call the server program, typ- ically  ./server.  In this mode the server reads an command from standard input, prints the response and waits for the next input.
● The second way of running the server is   where  is the way to call the server program, typ- ically  ./server, and  is the port on which the server listens for incoming connections.  A client program, which you will have to write as well, makes it possible to send commands to the server pro- gram and display the results on standard output. The client should be called with
without any quotes, e.g.
./client  localhost  2200  A  147 .188 .193 .15  22
All other ways of calling the client program should return an error message.


The speciﬁcation of a ﬁrewall rule is below. A rule is of the form.

where  is either a single IP address, which has the form. xxx .xxx .xxx .xxx, where xxx is a number between 0 and 255, or -,where  and  are IP addresses, and  is smaller than . Assume that IP addresses and ports are separated by exactly one space character.Similarly,  is either a single port number, which is a number between 0 and 65535, or -, where  and  are ports and  is smaller than .
Examples of such rules would be
147.188.193.0-147.188.194.255  21-22 147.188.192.41  443
Your server program should maximise the degree of concurrency and not contain any memory leaks.
Submission and Marking
● You should submit the ﬁle  server .c and client .c on the appropriate canvas-quiz.  The marking scripts will execute the command make with the Makeﬁle provided in the archive on canvas to produce all required binaries.
● The zip-archive on canvas contains a Makeﬁle and a basic test script. is provided in the ﬁle test .sh.  The Makeﬁle and the test script. will only work if server .c and client .c are in the same directory as the Makeﬁle and the test script. respectively.  The test script. tests the cases of adding a rule both interactively and via sockets.  It is run by changing into the directory containing the binaries and then running
./test .shWe will use more advanced scripts for marking which test all the speciﬁed functionality, including concurrency and memory leaks.  If the basic test script. does not work, all other scripts are likely to fail as well.
● Code which  does  not  compile  on the virtual  machine  provided will  be awarded 0 marks.
Hints
❼ You should start by implementing the interactive version of the server (the version running with server -i) and the R-command. Sockets and concurrency will be exp


● You may use the code provided in the lectures in your assignments as you see ﬁt.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
