<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Insert title here</title>
</head>
<script language="JavaScript">
win = window.location.href="Login";
</script>
</html>
--------------------
eror.js

function myFunction() {
	var x = document.getElementById("txtUserID").value;
	var y = document.getElementById("txtPassword").value;

	if (x == "") {
		document.getElementById("lblErrorMessage").innerHTML = "Error Message1";
		return false;
	} else if (y == "") {
		document.getElementById("lblErrorMessage").innerHTML = "Error Message2";
		return false;
	}
	return true;
}

function myFunction1() {
	document.getElementById("lblErrorMessage").innerHTML= "";
	var x = document.getElementById("txtUserID").value = "";
	var y = document.getElementById("txtPassword").value = "";

}
--------------------------------------
checkbox.js
function Check(chk) {
	if (document.myform.Check_All.value == "Check All") {
		for (i = 0; i < chk.length; i++)
			chk[i].checked = true;
		document.myform.Check_All.value = "";
	} else {

		for (i = 0; i < chk.length; i++)
			chk[i].checked = false;
		document.myform.Check_All.value = "Check All";
	}
}
----------------------------------
T003.jsp
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Insert title here</title>
</head>
<body>

	<div class="container">
		<h2 style="color: red;">Tranning</h2>
		<hr>
		<p>Login</p>
		<form action="Edit" method="post">
			<div class="form-group">
				<div class="col-sm-3">Welcome:</div>
				<div class="col-sm-offset-11">
					<a href="#">Logout</a>
				</div>
				<input class="form-control input-sm"
					style="background: blue; margin-bottom: 20px; color: #ffffff"
					value="Edit"></input>
			</div>
			<div class="form-group" style="text-align: center">
				<div class="row">
					<label for="pwd">Password:</label> <input />
				</div>
				<div class="row">
					<label for="pwd">Password:</label>
				</div>
				<div class="row">
					<label for="pwd">Password:</label>
				</div>
				<div class="row">
					<label for="pwd">Password:</label>
				</div>
				<div class="row">
					<label for="pwd">Password:</label>
				</div>
				<div class="row">
					<label for="pwd">Password:</label>
				</div>
			</div>

			<button type="submit" class="btn btn-default">Submit</button>
		</form>
	</div>

</body>
</html>
-------------------------
T002.jsp
<%@page import="java.sql.ResultSet"%>
<%@page import="javax.swing.JInternalFrame.JDesktopIcon"%>
<%@page import="fjs.cs.dao.MSTCUSTOMER_DAO"%>
<%@page import="fjs.cs.dao.MSTCUSTOMER"%>
<%@page import="java.io.PrintWriter"%>
<%@page import="fjs.cs.common.JdbcSQLServerConnection"%>
<%@page import="java.util.ArrayList"%>
<%@page import="java.sql.DriverManager"%>
<%@page import="java.sql.Statement"%>
<%@page import="java.sql.Connection"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Insert title here</title>
</head>
<head>
<title>Bootstrap Example</title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet"
	href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
<script
	src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script
	src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>
<style>
table {
	border-collapse: collapse;
	width: 100%;
}

th,td {
	padding: 8px;
	text-align: left;
	border-bottom: 1px solid #ddd;
}

tr:nth-child(even) {
	background-color: #ffffff;
}
</style>

<script type="text/javascript" src="WebContent/js/searchform.js"></script>
<script type="text/javascript" src="WebContent/js/checkbox.js"></script>
<body style="background: #66ffff">

	<div class="container">
		<h2 style="color: red;">Training</h2>
		<form class="form-group" action="Logout" method="post" name="myform">
			<div class="form-group">
				<div class="col-sm-3">
					Welcome:<%=session.getAttribute("txtUserID")%>
				</div>
				<div class="col-sm-offset-11">
					<a href="#">Logout</a>
				</div>
				<input class="form-control input-sm"
					style="background: blue; margin-bottom: 20px"></input>
			</div>
			<div class="form-group" style="background: #ffff33">
				<div class="col-sm-5">
					<label id="llbCustomername">Customer name:</label> <input
						id="txtCustomerName"> <label>Sex </label> <select
						id="llbSex">
						<option></option>
						<option>Male</option>
						<option>Female</option>
					</select>
				</div>
				<div class="col-sm-5">
					<label>Birthday:</label> <input id="txtBirthdayForm">~<input
						id="txtBirthdayTo">
				</div>
				<div class="col-sm-offset-11">
					<button id="btnSearch" type="button" class="btn"
						onclick="searchName()">Search</button>
				</div>
			</div>
			<div class="form-group">
				<div class="row-sm-12">
					<div class="col-sm-3">
						<button name="btnFirst" type="button" class="btn"><</button>
						<button name="btnPrevious" type="button" class="btn"><<</button>
						Previous
					</div>

					<div class="col-sm-offset-9">
						Next
						<button name="btnNext" type="button" class="btn">>></button>
						<button name="btnLast" type="button" class="btn">></button>

					</div>

				</div>
			</div>

			<table id="myTable" class="display">
				<thead>
					<tr>
						<th><input type="checkbox" name="Check_All" value="Check All"
							onClick="Check(document.myform.check_list)">
							
						</th>
						<th>Customer ID</th>
						<th>Customer Name</th>
						<th>Sex</th>
						<th>Birthday</th>
						<th>Address</th>
					</tr>
				</thead>
				<tbody>
					<%
						MSTCUSTOMER_DAO dao = new MSTCUSTOMER_DAO();
						for (MSTCUSTOMER customerlist : dao.getListCustomer()) {
					%>
					<tr>
						<td><input type="checkbox" name="check_list" class="styled"></td>
						<td><a href=""><%=(customerlist.getCustomer_ID() != null ? customerlist
						.getCustomer_ID() : "")%></a></td>
						<td><%=(customerlist.getCustomer_Name() != null ? customerlist
						.getCustomer_Name() : "")%></td>
						<td><%=(customerlist.getSex() != null ? customerlist
						.getSex() : "")%></td>
						<td><%=(customerlist.getBirthday() != null ? customerlist
						.getBirthday() : "")%></td>
						<td><%=(customerlist.getAddress() != null ? customerlist
						.getAddress() : "")%></td>
					</tr>
				</tbody>
				<%
					}
				%>
			</table>

			<br>
			<div class="form-group">
				<button name="btnAddnew" class="btn" type="button">Add New</button>
				<button name="btnDelete" class="btn" type="button">Delete</button>
			</div>




		</form>
	</div>

</body>

</html>
-------------------------
T001.jsp
<%@page
	import="com.sun.org.apache.xml.internal.security.transforms.params.InclusiveNamespaces"%>
<%@page import="com.sun.xml.internal.txw2.Document"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>T001_Login</title>
<script type="text/javascript" src="WebContent/js/error.js"></script>
</head>
<body style="background-color: #66ffff;">
	<div class="container"></div>
	<div class="panel panel-default">
		<div class="panel-heading">
			<h2 style="color: red;">Tranning</h2>
			<hr>
			<p>Login</p>
		</div>
		<div class="panel-body">
			<div class="row">
				<h2 style="text-align: center; color: blue">LOGIN</h2>
				<center>
					<p style="text-align: center">
						<label id="lblErrorMessage"></label>
					</p>
				</center>
			</div>

			<form class="form-control" name="myForm"
				onsubmit="return myFunction()" style="text-align: center"
				action="Login" method="post">
				<div class="row">
					<div class="form-group">
						<label>User Id:</label> <input
							<%=request.getAttribute("username")%> id="txtUserID"
							name="txtUserID" style="margin-left: 14px" type="text" value="" />
					</div>
					<div class="form-group" style="margin-top: 10px;">
						<label>Password:</label> <input
							<%=request.getAttribute("password")%> id="txtPassword"
							name="txtPassword" type="password" value="" />
					</div>
				</div>
				<div class="row">
					<div class="form-group" style="margin-top: 20px">
						<input type="submit" name="btnLogin" style="margin-left: 50px"
							value="Login" /> <input type="submit" name="btnClear"
							onclick="myFunction1()" style="margin-left: 100px" value="Clear" />
					</div>
				</div>

			</form>
		</div>
	</div>



</body>

</html>
----------------------
post logout
	protected void doPost(HttpServletRequest req, HttpServletResponse resp)
			throws ServletException, IOException {
		PrintWriter out = resp.getWriter();
		req.getRequestDispatcher(Constants.T001_LOGIN).include(req, resp);
		HttpSession session = req.getSession();
		session.invalidate();
		out.close();
	}

-------------------post login
	protected void doPost(HttpServletRequest req, HttpServletResponse resp)
			throws ServletException, IOException {
		// tao session
				HttpSession session = req.getSession();
				PrintWriter out = resp.getWriter();
				String username = req.getParameter("txtUserID");
				String password = req.getParameter("txtPassword");
				// xac thuc id va pass
				if (MSTUSER_DAO.validate(username, password)) {
					session.setAttribute("txtUserID", username);
					RequestDispatcher rd = req
							.getRequestDispatcher(Constants.T002_SEARCH);
					rd.forward(req, resp);
				} else {
					RequestDispatcher rd = req
							.getRequestDispatcher(Constants.T001_LOGIN);
					rd.forward(req, resp);
				}
				out.close();
			}
-------------------
connection
	
	    private static String dbURL = "jdbc:sqlserver://localhost:1433;" + "databaseName=CustomerSystem";
	    private static String userName = "sa";
	    private static String password = "Abc12345";
	 
	  
	    public static void main(String args[], String userName) {
	       System.out.println(getConnection());
	    }
	 

	    public static Connection getConnection() {
	        Connection conn = null;
	        try {
	        	//khai bao class Driver
	            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
	            conn = DriverManager.getConnection(dbURL, userName, password);
	        } catch (Exception ex) {
	            ex.printStackTrace();
	            System.out.println("Loiiiiiiiiiii");
	        }
	        return conn;
	    }
-----------------------
	// T001(Login)
	public static final String T001_LOGIN = "/WEB-INF/jsp/T001.jsp";
	// T002(Search)
	public static final String T002_SEARCH = "/WEB-INF/jsp/T002.jsp";
	// T002(Edit)
	public static final String T003_EDIT = "/WEB-INF/jsp/T003.jsp";
-------------------
protected void doGet(HttpServletRequest req, HttpServletResponse resp)
			throws ServletException, IOException {
		RequestDispatcher myRD = null;
		// Hien thi man hinh Login
		myRD = req.getRequestDispatcher(Constants.T001_LOGIN);
		myRD.forward(req, resp);

	}
--------------------------
public ArrayList<MSTCUSTOMER> getListCustomer() {
		Connection conn = JdbcSQLServerConnection.getConnection();
		String sql = "SELECT * FROM MSTCUSTOMER";
		ArrayList<MSTCUSTOMER> list = new ArrayList<MSTCUSTOMER>();
		try {
			PreparedStatement ps = (PreparedStatement) conn
					.prepareStatement(sql);
			ResultSet rs = ps.executeQuery();
			while (rs.next()) {
				MSTCUSTOMER mstcustomer = new MSTCUSTOMER() {
				};
				mstcustomer.setCustomer_ID(rs.getString("CUSTOMER_ID"));
				mstcustomer.setCustomer_Name(rs.getString("CUSTOMER_NAME"));
				mstcustomer.setSex(rs.getString("SEX"));
				mstcustomer.setBirthday(rs.getString("BIRTHDAY"));
				mstcustomer.setAddress(rs.getString("ADDRESS"));
				list.add(mstcustomer);
			}
			conn.close();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return list;
	}

----------------------
public String psn_CD;
	public String userID;
	public String password;
	public String username;
	public String delete_YMD;
	public String insert_YMD;
	public String insert_PSN_CD;
	public String update_YMD;
	public String update_PSN_CD;
----------------
public String customer_ID;
	public String customer_Name;
	public String sex;
	public String birthday;
	public String email;
	public String address;
	public String delete_YMD;
	public String insert_YMD;
	public String insert_PSN_CD;
	public String update_YMD;
	public String update_PSN_CD;
--------------------
