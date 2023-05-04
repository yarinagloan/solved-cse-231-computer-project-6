Download Link: https://assignmentchef.com/product/solved-cse-231-computer-project-6
<br>
This assignment focuses on the design, implementation and testing of a Python program that uses lists and tuples.




<strong>Assignment Overview </strong>

<strong> </strong>

In this assignment, you will practice with lists and tuples.




<h2>Assignment Background</h2>

<strong> </strong>

Dr. Enbody is a hockey player and fan so this project is about hockey statistics using data from the National Hockey League (nhl.com).  In hockey one important statistic is the number of points that a player gets in a game; points are the sum of the goals scored and the number of goals that the player assisted in scoring (called an “assist” and means that the player passed to another player who scored).  In hockey total points is almost as important as total goals scored.  This data set has the top players with respect to points-per-game over their career, but only considering players who played at least 100 games.  The data is <strong>not</strong> sorted by points-per-game.




<h2>Assignment Specifications</h2>

<strong> </strong>

You will develop a Python program that extracts and displays statistics from a data file.  The basic concept is that you will read <em>all</em> the data into a list of lists and then extract data of interest from that master_list.  We provide a file which is in the comma-separated-value format (file extension is .csv).  You can open the file to look at it using a spreadsheet program such as Excel.




<strong>open_file () </strong>à<strong> file pointer:</strong>

<ol>

 <li>This function takes no arguments, prompts for a file name and returns the file pointer to that file. The function will keep asking until a file is found.  Use try-except and FileNotFoundError.</li>

 <li>Parameters: none</li>

 <li>Returns : file pointer</li>

 <li>The function displays a prompt and possibly an error message.</li>

</ol>




<strong>read_file (fp) </strong>à<strong> list of lists:</strong>

<ol>

 <li>This function accepts a file pointer and returns a master list of lists of all the data in the file. Each line of the file will be a list in the master list. The master list will be in the same order that the data is in the file. The file is a comma-separated-value file (.csv).  However, some data fields have commas so you must use the csv module:</li>

</ol>




import csv   # place this line at the top of the program file




#place these lines in this function reader = csv.reader(fp) for line_list in reader:  # note that using csv.reader you get a list!




<ol>

 <li>Parameters: file pointer</li>

 <li>Returns : master_list (list of lists)</li>

 <li>The function displays nothing.</li>

</ol>




<strong>shoots_left_right(master_list)</strong>à<strong> (int,int):</strong>

<ol>

 <li>This function accepts as input the master list and returns two integers representing the count of players who shoot left and those who shoot right. Return the data in that order. This data is found in the column labeled “S/C” in the file.</li>

</ol>

Algorithm: read each list in the master_list, extract the “S/C” data from index 1, and count whether the player shoots left or right.

<ol>

 <li>Parameters: master_list (list of lists)</li>

 <li>Returns : int, int</li>

 <li>The function displays nothing.</li>

</ol>




<h2>position(master_list)—à (int,int,int,int)</h2>

<ol>

 <li>This function accepts as input the master list and returns four integers representing the count of players who play positions left-wing (“L”), right-wing (“R”), center (“C”), and defense (“D”). Return the data in that order. This data is found in the column labeled “Pos” in the file.  The algorithm is similar to the previous function.</li>

 <li>Parameters: master_list (list of lists)</li>

 <li>Returns : int, int, int, int</li>

 <li>The function displays nothing.</li>

</ol>




<h2>off_side_shooter(master_list)—à (int,int)</h2>

<ol>

 <li>This function accepts as input the master list and returns two integers representing the count of players who play the left-wing position (“L”) but shoot right (“R”) and those who play the right-wing position (“R”) but shoot left (“L”). Return the data in that order. This data is found in the column labeled  “S/C” for shooting data and “Pos” for the position data in the file.  The algorithm is similar to the previous function.</li>

 <li>Parameters: master_list (list of lists)</li>

 <li>Returns : int, int</li>

 <li>The function displays nothing.</li>

</ol>




<h2>points_per_game(master_list)—à list of tuples</h2>

<ol>

 <li>This function accepts as input the master list and returns a sorted list of tuples where each tuple is of the form:</li>

</ol>

(points-per-game, player name, position)

The list will be <strong>sorted</strong> on points-per-game (highest to lowest) and only the <strong>top ten</strong> are returned, i.e. the list contains ten tuples in decreasing, sorted order.  The player name is in the first column, i.e. labeled “Player” whereas the points-per-game is in the column labeled “P/GP” (which stands for Points/Games_Played).  <em>You must convert points-pergame to a float </em>before sorting. Python sorts on the first item in the tuple (which is what you want in this case).  Remember to sort in decreasing order.  You can use slicing to extract the first (top) ten from the sorted list. (Optional: if you want a challenge, you can write this function in one line; list comprehension is useful.)

<ol>

 <li>Parameters: master_list (list of lists)</li>

 <li>Returns : list of tuples</li>

 <li>The function displays nothing.</li>

</ol>




<h2>games_played(master_list)—à list of tuples</h2>

<ol>

 <li>This function accepts as input the master list and returns a sorted list of tuples where each tuple is of the form:</li>

</ol>

(games played, player name)

The list will be <strong>sorted</strong> on games played (highest to lowest) and only the <strong>top ten</strong> are returned, i.e. the list contains ten tuples in decreasing, sorted order.  The games played is in the column labeled “GP”.  The challenge of this function is that some players have played over a thousand games so commas appear in the values.  <em>You must remove the comma and convert to an integer before sorting</em>. (Optional: if you want a further challenge, you can write this function in one line; list comprehension is useful.)

<ol>

 <li>Parameters: master_list (list of lists)</li>

 <li>Returns : list of tuples</li>

 <li>The function displays nothing</li>

</ol>

<strong> </strong>

<h2>shots_taken(master_list)—à list of tuples</h2>

<ol>

 <li>This function accepts as input the master list and returns a sorted list of tuples where each tuple is of the form:</li>

</ol>

(shots taken, player name)

The list will be <strong>sorted</strong> on shots taken (highest to lowest) and only the <strong>top ten</strong> are returned, i.e. the list contains ten tuples in decreasing, sorted order.  The shots taken is in the column labeled “S”.  As in the previous function, some players have taken over a thousand shots so commas appear in the values so again you must remove the comma and convert to an integer before sorting.  <em>However, the new challenge in this function is that some data is missing</em> (indicated by a pair of hyphens “–“) so you must skip that data, i.e. ignore that player. In the earlier years of the NHL this data wasn’t recorded. (Optional: if you want a further challenge, you can write this function in one line; list comprehension is useful.)

<ol>

 <li>Parameters: master_list (list of lists)</li>

 <li>Returns : list of tuples</li>

 <li>The function displays nothing</li>

</ol>

<strong> main():  </strong>

This function calls the above functions, first to open the file and read the data, and then to display the values.  Data will be displayed in the order of the functions above.  We provide a file named strings.txt that has the strings and the formatting for printing the data. Note that in order to print data in the thousands a comma is included in the format string, e.g.

“{:&lt;20s}{:&gt;16,d}”




<h3>Assignment Notes and Hints</h3>




<ol>

 <li>The coding standard for CSE 231 is posted on the course website:</li>

</ol>




<a href="https://www.cse.msu.edu/%7Ecse231/General/coding.standard.html">http://www.cse.msu.edu/~cse231/General/coding.standard.html</a>




Items 1-9 of the Coding Standard will be enforced for this project.




<ol start="2">

 <li>The program will produce reasonable and readable output, with appropriate labels for all values displayed.</li>

</ol>




<ol start="3">

 <li>We provide a py program for you to start with.</li>

</ol>




<ol start="4">

 <li>If you “hard code” answers, you will receive a grade of zero for the whole project. An example of hard coding is to simply print the approximate value of e rather than calculating it and then printing the calculated average.</li>

</ol>

<strong> </strong>

<h3>Suggested Procedure</h3>

<strong> </strong>




<em>The last version of your solution is the program which will be graded by your TA. </em>

<em> </em>

<em>You should use the <strong>Mimir</strong> system to back up your partial solutions, especially if you are working close to the project deadline.  That is the easiest way to ensure that you won’t lose significant portions of your work if your machine fails or there are other last-minute problems. </em>

<strong> </strong>

<strong> </strong>

<h3>Assignment Deliverable</h3>




The deliverable for this assignment is the following file:




proj06.py – the source code for your Python program




Be sure to use the specified file name and to submit it for grading via the <strong>Mimir</strong> <strong>system</strong> before the project deadline.







Sample Output




<strong>Function Test read_file(): </strong>

<strong>Input:</strong> “scoring_short.csv”

<strong>Output: </strong>

[[‘Adam Oates’, ‘R’, ‘C’, ‘1,337’, ‘341’, ‘1,079’, ‘664’, ‘415’, ‘1,420’,

‘2,392’, ‘415’, ’79’, ‘210’, ‘10,512:35’, ‘0.26’, ‘0.81’, ‘0.5’, ‘0.31’,

‘1.06’, ‘1.79’, ‘0.31’, ‘–‘, ‘–‘, ‘–‘], [‘Alex Ovechkin’, ‘R’, ‘L’,

‘1,129’, ‘684’, ‘569’, ‘351’, ‘218’, ‘1,253’, ‘5,444’, ‘711’, ‘2,972’, ‘438’,

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’,

‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’, ‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]]




<strong>      </strong>




<strong>Function Test shoots_left_right(): Input:</strong>

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’, ‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’, ‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]]




<strong>Output: </strong>

(9, 5)




<strong>      </strong>

<strong>Function Test position(): Input:</strong>

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’, ‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’, ‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]]




<strong>Output: </strong>

(3, 2, 8, 1)







<strong>      </strong>

<strong>Function Test off_side_shooter(): Input:</strong>

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’, ‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’, ‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]]




<strong>Output: </strong>

(2, 1)







<strong>      </strong>

<strong>Function Test points_per_game(): Input:</strong>

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’, ‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’, ‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]]




<strong>Output: </strong>

[(1.39, ‘Bobby Orr’, ‘D’), (1.33, ‘Connor McDavid’, ‘C’), (1.13, ‘Bernie

Federko’, ‘C’), (1.11, ‘Bryan Trottier’, ‘C’), (1.11, ‘Alex Ovechkin’, ‘L’),

(1.1, ‘Brett Hull’, ‘R’), (1.1, ‘Bobby Hull’, ‘L’), (1.07, ‘Bernie Nicholls’, ‘C’), (1.06, ‘Bobby Clarke’, ‘C’), (1.06, ‘Adam Oates’, ‘C’)]







<strong>      </strong>

<strong>Function Test games_played(): Input:</strong>

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’, ‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’,

‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]] <strong> </strong>

<strong>Output: </strong>

[(1337, ‘Adam Oates’), (1279, ‘Bryan Trottier’), (1269, ‘Brett Hull’), (1144,

‘Bobby Clarke’), (1129, ‘Alex Ovechkin’), (1127, ‘Bernie Nicholls’), (1063,

‘Bobby Hull’), (1000, ‘Bernie Federko’), (990, ‘Alexander Mogilny’), (657, ‘Bobby Orr’)]







<strong>      </strong>

<strong>Function Test shots_taken(): Input:</strong>

‘23,635:51’, ‘0.61’, ‘0.5’, ‘0.31’, ‘0.19’, ‘1.11’, ‘4.82’, ‘0.63’, ‘2.63’,

‘0.39’, ’20:56′], [‘Alexander Mogilny’, ‘L’, ‘R’, ‘990’, ‘473’, ‘559’, ‘374’,

‘185’, ‘1,032’, ‘2,966’, ‘432’, ‘281’, ’68’, ‘8,418:43’, ‘0.48’, ‘0.56’,

‘0.38’, ‘0.19’, ‘1.04’, ‘3’, ‘0.44’, ‘–‘, ‘–‘, ‘–‘], [‘Artemi Panarin’,

‘R’, ‘L’, ‘365’, ‘140’, ‘241’, ‘151’, ’90’, ‘381’, ‘949’, ‘114’, ‘114’, ’72’,

‘7,150:45’, ‘0.38’, ‘0.66’, ‘0.41’, ‘0.25’, ‘1.04’, ‘2.6’, ‘0.31’, ‘0.31’,

‘0.2’, ’19:35′], [‘Auston Matthews’, ‘L’, ‘C’, ‘257’, ‘142’, ‘117’, ’75’,

’42’, ‘259’, ‘886’, ’44’, ’89’, ‘213’, ‘4,742:55’, ‘0.55’, ‘0.46’, ‘0.29’,

‘0.16’, ‘1.01’, ‘3.45’, ‘0.17’, ‘0.35’, ‘0.83’, ’18:27′], [‘Bernie Federko’,

‘L’, ‘C’, ‘1,000’, ‘369’, ‘761’, ‘469’, ‘292’, ‘1,130’, ‘2,074’, ‘487’, ‘0’,

‘0’, ‘–‘, ‘0.37’, ‘0.76’, ‘0.47’, ‘0.29’, ‘1.13’, ‘2.07’, ‘0.49’, ‘–‘, ‘–‘,

‘–‘], [‘Bernie Nicholls’, ‘R’, ‘C’, ‘1,127’, ‘475’, ‘734’, ‘458’, ‘276’,

‘1,209’, ‘3,231’, ‘1,292’, ’65’, ’25’, ‘1,011:55’, ‘0.42’, ‘0.65’, ‘0.41’,

‘0.24’, ‘1.07’, ‘2.87’, ‘1.15’, ‘–‘, ‘–‘, ‘–‘], [‘Bill Cowley’, ‘L’, ‘C’,

‘549’, ‘195’, ‘354’, ‘253’, ’99’, ‘549’, ‘–‘, ‘143’, ‘0’, ‘0’, ‘–‘, ‘0.36’,

‘0.64’, ‘0.46’, ‘0.18’, ‘1’, ‘–‘, ‘0.26’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Clarke’,

‘L’, ‘C’, ‘1,144’, ‘358’, ‘852’, ‘541’, ‘311’, ‘1,210’, ‘2,582’, ‘1,453’, ‘0’,

‘0’, ‘–‘, ‘0.31’, ‘0.74’, ‘0.47’, ‘0.27’, ‘1.06’, ‘2.26’, ‘1.27’, ‘–‘, ‘–‘,

‘–‘], [‘Bobby Hull’, ‘L’, ‘L’, ‘1,063’, ‘610’, ‘560’, ‘366’, ‘194’, ‘1,170’,

‘4,577’, ‘634’, ‘0’, ‘0’, ‘–‘, ‘0.57’, ‘0.53’, ‘0.34’, ‘0.18’, ‘1.1’, ‘4.31’,

‘0.6’, ‘–‘, ‘–‘, ‘–‘], [‘Bobby Orr’, ‘L’, ‘D’, ‘657’, ‘270’, ‘645’, ‘326’,

‘319’, ‘915’, ‘3,058’, ‘953’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.98’, ‘0.5’, ‘0.49’, ‘1.39’, ‘4.65’, ‘1.45’, ‘–‘, ‘–‘, ‘–‘], [‘Brett Hull’, ‘R’, ‘R’, ‘1,269’,

‘741’, ‘650’, ‘388’, ‘262’, ‘1,391’, ‘4,876’, ‘458’, ‘142’, ‘122’, ‘9,648:19’,

‘0.58’, ‘0.51’, ‘0.31’, ‘0.21’, ‘1.1’, ‘3.84’, ‘0.36’, ‘–‘, ‘–‘, ‘–‘],

[‘Bryan Trottier’, ‘L’, ‘C’, ‘1,279’, ‘524’, ‘901’, ‘542’, ‘359’, ‘1,425’,

‘2,841’, ‘912’, ‘0’, ‘0’, ‘–‘, ‘0.41’, ‘0.7’, ‘0.42’, ‘0.28’, ‘1.11’, ‘2.22’,

‘0.71’, ‘–‘, ‘–‘, ‘–‘], [‘Connor McDavid’, ‘L’, ‘C’, ‘333’, ‘152’, ‘290’,

‘184’, ‘106’, ‘442’, ‘1,017’, ‘110’, ‘142’, ‘133’, ‘7,149:33’, ‘0.46’, ‘0.87’,

‘0.55’, ‘0.32’, ‘1.33’, ‘3.05’, ‘0.33’, ‘0.43’, ‘0.4’, ’21:28′]] <strong> </strong>

<strong>Output: </strong>

[(5444, ‘Alex Ovechkin’), (4876, ‘Brett Hull’), (4577, ‘Bobby Hull’), (3231,

‘Bernie Nicholls’), (3058, ‘Bobby Orr’), (2966, ‘Alexander Mogilny’), (2841,

‘Bryan Trottier’), (2582, ‘Bobby Clarke’), (2392, ‘Adam Oates’), (2074, ‘Bernie Federko’)]




<strong>             </strong>




<strong>Test 1: </strong>

<strong>Enter filename: Scoring_per_Game.csv </strong>

<strong>  Shooting  left:    39 right:   25    Position   left:       7 right:     18 center:    36 defense:    3 </strong>

<strong> </strong>

<strong>    Off-side Shooter     left-wing shooting right:    2 right-wing shooting left:    8 </strong>

<strong> </strong>

<strong>      Top Ten Points-Per-Game        </strong>

<strong>Player              Position Points Per Game </strong>

<strong>Wayne Gretzky              C            1.92 </strong>

<strong>Mario Lemieux              C            1.88 </strong>

<strong>Mike Bossy                 R            1.50 </strong>

<strong>Joe Malone                 C            1.40 </strong>

<strong>Bobby Orr                  D            1.39 </strong>

<strong>Connor McDavid             C            1.33 </strong>

<strong>Marcel Dionne              C            1.31 </strong>

<strong>Sidney Crosby              C            1.28 </strong>

<strong>Peter Stastny              C            1.27 </strong>

<strong>Peter Forsberg             C            1.25 </strong>

<strong> </strong>

<strong>        Top Ten Games-Played         </strong>

<strong>Player                  Games Played </strong>

<strong>Gordie Howe                    1,767 </strong>

<strong>Mark Messier                   1,756 </strong>

<strong>Jaromir Jagr                   1,733 </strong>

<strong>Ron Francis                    1,731 </strong>

<strong>Steve Yzerman                  1,514 </strong>

<strong>Wayne Gretzky                  1,487 </strong>

<strong>Teemu Selanne                  1,451 </strong>

<strong>Paul Coffey                    1,409 </strong>

<strong>Stan Mikita                    1,396 </strong>

<strong>Joe Sakic                      1,378 </strong>

<strong> </strong>

<strong>        Top Ten Shots-Taken          </strong>

<strong>Player                   Shots Taken </strong>

<strong>Jaromir Jagr                   5,637 </strong>

<strong>Alex Ovechkin                  5,444 </strong>

<strong>Marcel Dionne                  5,363 </strong>

<strong>Phil Esposito                  5,166 </strong>

<strong>Wayne Gretzky                  5,088 </strong>

<strong>Brett Hull                     4,876 </strong>

<strong>Joe Sakic                      4,621 </strong>

<strong>Steve Yzerman                  4,602 </strong>

<strong>Bobby Hull                     4,577 </strong>

<strong>Teemu Selanne                  4,540  </strong>

<strong> </strong>

<h3>Grading Rubric</h3>




Computer Project #06                           Scoring Summary

General Requirements:

( 4 pts) Coding Standard 1-9

(descriptive comments, function headers, mnemonic identifiers, format, etc…)




Implementation:

( 4 pts)  open_file function (no Mimir test)




( 4 pts)  read_file function




( 4 pts)  shoots_left_right function




( 4 pts)  position function




( 4 pts)  off_side_shooter function




( 4 pts)  points_per_game function




( 4 pts)  games_played function




( 4 pts)  shots_taken function




( 9 pts)  Test 1







Note: hard coding an answer earns zero points for the whole project -10 points for not using main()