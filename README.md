Download Link: https://assignmentchef.com/product/solved-cs202-homework-5-graphs
<br>
The details of the member functions are as follows:

<ul>

 <li><strong>FriendNet(const string fileName); </strong></li>

</ul>

The default constructor loads a friendship network from an input file called <strong>fileName</strong>. The first row of this file indicates the number of people in the network and each subsequent row includes information of a particular person. This information contains &lt;id&gt; &lt;name&gt; &lt;degree&gt; &lt;friend_id&gt; tokens separated by white space. For a particular person <em>P</em>,

<ul>

 <li><strong>&lt;id&gt;</strong> and <strong>&lt;name&gt;</strong> are the id and the name of person <em>P</em>, respectively.</li>

 <li><strong>&lt;degree&gt; </strong>is the number of friends of person <em>P</em>.</li>

 <li><strong>&lt;friend_id&gt; </strong>is the id of a friend of person <em>P</em>. Note that a person may have zero or more friends and there will be exactly <strong>&lt;degree&gt;</strong> friend ids after the degree token.</li>

</ul>




In this assignment, you may assume that the contents of the input file are always valid. You may also assume that the ids and the names are unique and the ids are in the range of 0 and N – 1, where N is the number of people in the network. You may also assume that all names are case sensitive and do not contain any spaces, e.g., John Doe is written as JohnDoe in the file.




Note that, if the input file <strong>fileName</strong> does not exist, then the default constructor creates an empty friendship network.




As an example, the table shown on the left is an input file for the network illustrated on the right. This file contains 17 people, as indicated in its first line. For example, the fifth line of this file indicates that the person with an id of 3 has the name of Dogan and has four friends, with the ids of 14, 0, 1, and 2.




<table width="609">

 <tbody>

  <tr>

   <td width="257">


    <table width="253">

     <tbody>

      <tr>

       <td width="253">170    Ali     4 1 14 3 21    Beril 2 0 32    Cigdem  4 10 14 0 33    Dogan  4 14 0 1 24    Ebru    2 16 75    Funda 06    Gamze 1 117    Hande 2 16 48    Ibrahim 2 10 139    Jale 4 12 11 13 1010  Kenan 5 2 13 12 8 911  Leman 3 15 9 612  Mahmut 3 10 9 1513  Nalan 3 9 10 814  Okan 3 2 0 315  Pinar 2 12 1116  Rana 2 4 7</td>

      </tr>

     </tbody>

    </table></td>

   <td width="352"></td>

  </tr>

 </tbody>

</table>




<ul>

 <li><strong>void listFriends(const string personName, const int hopNo); </strong></li>

</ul>




It lists the names of all people that are accessible from a given person, whose name is <strong>personName</strong>, within the given number <strong>hopNo</strong> of hops (i.e., using at most hopNo edges). If this given person does not take place in the friendship network, give a warning message. If the given number of hops is nonpositive, do not list any people. See the output example below for the format. You may assume that the names are unique within the friendship network.

<ul>

 <li><strong>void displayAverageDegrees(); </strong></li>

</ul>

It calculates and displays the average degree of each connected component within the friendship network. The degree of a vertex is defined as the number of its neighbors. The average degree of a connected component is the mean of the degrees computed for every vertex in this connected component.  See the output example below for the format.

<ul>

 <li><strong>void displayDiameters(); </strong></li>

</ul>

It calculates and displays the diameter of each connected component within the friendship network. The diameter of a connected component is the longest of the shortest paths between any pair of vertices within this connected component. See the output example below for the format

Below is an example test program that uses this class and the corresponding output. This test program uses the friendship network illustrated above. Assume that the name of the input file is “friends.txt”. Of course, use other programs to test your implementation.

<table width="672">

 <tbody>

  <tr>

   <td width="672">#include &lt;iostream&gt; using namespace std; #include “FriendNet.h” int main(){FriendNet F(“friends.txt”); F.listFriends(“Selim”, 2);F.listFriends(“Funda”, 1);    F.listFriends(“Cigdem”, -1);    cout &lt;&lt; endl; F.listFriends(“Ibrahim”, 2);F.listFriends(“Ibrahim”, 3);    cout &lt;&lt; endl; F.displayAverageDegrees();    cout &lt;&lt; endl;F.displayDiameters();    cout &lt;&lt; endl; return 0;}</td>

  </tr>

 </tbody>

</table>







The output of this program will be as follows.

<table width="688">

 <tbody>

  <tr>

   <td width="688">Selim does not exist in the network.People accessible from Funda within 1 hops: NOBODYPeople accessible from Cigdem within -1 hops: NOBODYPeople accessible from Ibrahim within 2 hops: Cigdem, Jale, Kenan, Mahmut, NalanPeople accessible from Ibrahim within 3 hops: Ali, Cigdem, Dogan, Jale, Kenan,Leman, Mahmut, Nalan, Okan, Pinar There are 3 connected components. The average degrees are:For component 0: 3.08For component 1: 2.00For component 2: 0.00 There are 3 connected components. The diameters are:For component 0: 6For component 1: 1 For component 2: 0</td>

  </tr>

 </tbody>

</table>


