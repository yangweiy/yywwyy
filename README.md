# yywwyy
112233
yyy
package ParkingSystem;

import java.util.ArrayList;
//ej
public interface IParams {
    int big = 0;
    int medium=0;
    int small=0;
    ArrayList<Integer>PlanParking=new ArrayList<>();
    public void set(int big,int medium,int small);
    public int getBig();
    public int getMedium();
    public int getSmall();
    public ArrayList<Integer> getPlanParking();
    public void add(int i);
}

package ParkingSystem;

import java.util.ArrayList;
import java.util.Scanner;

public interface IParking {
    
    public void print();
//检查是否有carType对  应的停车位
//如果没有空车位，请返回false，否则将该车停入车位并返回true   
public boolean addCar(int carType);
public static IParams parse() throws Exception{
IParams pr=new IParams() {
    int big = 0;
    int medium=0;
    int small=0;
    ArrayList<Integer>PlanParking=new ArrayList<>();
    public int getBig() {
        return big;
    }
    public void set(int big,int medium,int small) {
        this.big=big;
        this.medium=medium;
        this.small=small;
    }
    public int getMedium() {
        return medium;
    }

    public int getSmall() {
        return small;
    }
    public void add(int i){
        IParking.add(i);
    }
    public ArrayList<Integer> getPlanParking() {
        return PlanParking;
    }
};

int k=0,sum=0;//sum: addCar数   k字符串的定位 截断
Scanner sc=new Scanner(System.in);
String init_code=sc.nextLine(),add_code,car_num,add_num,temp;
while((k=init_code.indexOf( "addCar",k))!=-1){
    sum++;
    k+=6;
}
add_code=sc.nextLine();
car_num=add_code.substring(2,add_code.indexOf("]",2));
car_num=car_num+",";
k=0;
int[] num =new int[3];
for(int i=0;i<3;i++){
    temp=car_num.substring(k,car_num.indexOf(",",k)).trim();
    k=car_num.indexOf(",",k)+1;
    num[i]=Integer.parseInt(temp);
}
pr.set(num[0],num[1],num[2]);

add_num=add_code.substring(add_code.indexOf("]",2)+1,add_code.length()-1);
k=0;int j=0;
for(int i=0;i<add_num.length();i++){
    if(add_num.charAt(i)>='1'&&add_num.charAt(i)<='3'){
        j++;
        pr.add(add_num.charAt(i)-48);
    }
}
if(j!=sum){
    System.err.println("车辆数不符");
}
sc.close();
return pr;
}
public static void add(int i) {
	// TODO Auto-generated method stub
	
}
}


package ParkingSystem;
//good  
public class ParkingSystem {

}

