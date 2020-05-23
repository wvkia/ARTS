### Algorithm


####  q001两数之和

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

1、简单暴力破解，循环两层，所以时间复杂度 O(n*2)

```java
public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length ;i++){
            for(int j=i+1; j < nums.length ; j++){
                if(nums[i] + nums[j] == target){
                    return new int[]{i,j};
                }
            }
        }
        return null;
    }
```

2、因为y = target-x，我们可以利用Map集合来处理，就是循环的时候到map中查询target-x有没有作为key的，如果有说明可以找到，否则就把target-x加入到map中，等待后面的拿到新插入的值作为剩余数

```java

public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> map=new HashMap();
        for(int i = 0; i< nums.length; i++){
            if(map.containsKey(target-nums[i])){
                return new int[]{i,map.get(target-nums[i])};
            }
            map.put(nums[i],i);
        }
        return new int[2];
    }
```

### Review

``https://www.recordedfuture.com/dark-web-reality/``文章主要介绍了darkweb以及关于darkweb的一些谣言。darkweb并非我们所想象的是一个黑暗的网站聚集地，实际上更像一团无序的毛线团，只不过中间的某些节点存在非法的网站。


### Tips

工作中遇到一个Left join的问题，因为left join的左表是一张大表，右表是一张小表，虽然有字段限制，但由于两张表的字符集不一致，导致索引失效，从而导致中间temp表猛增，数据库卡住，造成生产事故。

### Share

分享JVM的看书流程，我们知道一段C代码需要编译、链接、运行，而Java代码也是一样，需要编译链接运行，只不过C代码是在实际物理硬件上运行，而Java代码是在JVM上运行，JVM再映射到物理机具体指令。Java的编译就对应生存Class文件，然后由JVM将这个Class文件加载到内存中，获取具体类信息，就是类加载机制；然后将符号引用转化成具体方法区内存地址，完成后再进行初始化，初始化阶段就是对将要用到的类准备好。实际运行时，涉及JVM内存结构，因为我们不需要像C语言那样自己管理内存，都是由JVM自动管理，所以涉及JVM内存管理；运行时需要完成对字节码指令的解析，就是JVM执行引擎。
