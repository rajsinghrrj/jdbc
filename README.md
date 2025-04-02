# jdbc
## jdbc connection code
package jdbc_Example;

import java.sql.*;

public class jdbcconnection 
{
    public static void main(String[] args) 
    {
        // Database connection details
        String url = "jdbc:mysql://localhost:3306/Company"; // Replace with your DB name
        String username = "root"; // Your MySQL username
        String password = "raj@123"; // Your MySQL password

        // SQL query string
        // Replace with your table name

        // Initialize JDBC objects
        Connection connn = null;
        Statement stmt = null;
        ResultSet rs = null;

        try {
            // 1. Establish connection to the database
             Connection conn = DriverManager.getConnection(url, username, password);
            System.out.println("Connection to the database established successfully.");

            // 2. Create a statement object
            stmt = conn.createStatement();

            // 3. Execute the query
            String query = "SELECT * FROM emp";
            rs = stmt.executeQuery(query);

            // 4. Process the result set
            while (rs.next()) {
                // Assuming your table has columns "id" and "name" for demonstration
                int id = rs.getInt("id");
                String name = rs.getString("name");
                System.out.println("ID: " + id + ", Name: " + name);
            }

        } 
        catch (SQLException e) 
        {
            // Handle SQL exceptions
            System.out.println("SQL Exception: " + e.getMessage());
        } 
        finally 
        {
            // 5. Close resources
            try {
                if (rs != null) rs.close();
                if (stmt != null) stmt.close();
                if (connn != null) connn.close();
            } 
            catch (SQLException e) 
            {
                System.out.println("Error closing resources: " + e.getMessage());
            }
        }
    }
}

### update code in jdbc
package jdbc_Example;


import java.sql.*;

public class updateClass 
{
    public static void main(String[] args) 
    {
        // Database connection details
        String url = "jdbc:mysql://localhost:3306/Company"; // Replace with your DB name
        String username = "root"; // Your MySQL username
        String password = "raj@123"; // Your MySQL password

        // SQL query string
        // Replace with your table name

        // Initialize JDBC objects
        Connection conn = null;
        Statement stmt = null;
        ResultSet rs = null;
        //RowsAffected=rowsAffected=null;

        try {
            // 1. Establish connection to the database
            conn = DriverManager.getConnection(url, username, password);
            System.out.println("Connection to the database established successfully.");

            // 2. Create a statement object
            stmt = conn.createStatement();

            // 3. Execute the query
            //String query = "SELECT * FROM emp";
            String updateQuery = "UPDATE emp SET name = 'RRJ Singh', branch = 'CSE' WHERE id = 2";
        
        
            int rowsAffected = stmt.executeUpdate(updateQuery);

            // 4. Process the result set
            if (rowsAffected > 0) {
                System.out.println("Employee data updated successfully.");
            } else {
                System.out.println("No rows were updated.");
            }
            

        } 
        catch (SQLException e) 
        {
            // Handle SQL exceptions
            System.out.println("SQL Exception: " + e.getMessage());
        } 
        finally 
        {
            // 5. Close resources
            try {
                if (rs != null) rs.close();
                if (stmt != null) stmt.close();
                if (conn != null) conn.close();
            } 
            catch (SQLException e) 
            {
                System.out.println("Error closing resources: " + e.getMessage());
            }
        }
    }
}


