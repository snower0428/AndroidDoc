
# 常用控件

**android:gravity 和 android:layout_gravity的区别**

- **android:gravity**是对该View内容的限定，比如一个Button上面的text,
  可以设置text靠左，靠右等。
- **android:layout_gravity**是用来设置该view相对父view的位置。

## TextView

## Button
> 禁用英文字母自动大写转换，android:textAllCaps="false"

## EditText

## ImageView

## ProgressBar
> 通过style属性可以指定不同的样式，比如指定水平进度条：

```xml
    <ProgressBar
        android:id="@+id/progress_bar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        style="?android:attr/progressBarStyleHorizontal"
        android:max="100"/>
```

## AlertDialog

```java
    AlertDialog.Builder alertDialog = new AlertDialog.Builder(MainActivity.this);
        alertDialog.setTitle("This is Dialog");
        alertDialog.setMessage("This is Message");
        alertDialog.setCancelable(false);
        alertDialog.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                // 处理点击事件
            }
        });
        alertDialog.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialogInterface, int i) {
                // 处理点击事件
            }
        });
        alertDialog.show();
```

## ProgressDialog
> ProgressDialog和AlertDialog有点类似，
> 都可以在界面上弹出一个对话框，都能够屏蔽掉其它控件的交互能力。
> 不同的是，ProgressDialog会在对话框中显示一个进度条。

```java
    ProgressDialog progressDialog = new ProgressDialog(MainActivity.this);
    progressDialog.setTitle("This is ProgressDialog");
    progressDialog.setMessage("Loading...");
    progressDialog.setCancelable(true);
    progressDialog.show();
```

> 注意，如果在setCancelable()中传入了false，
> 表示ProgressDialog是不能通过Back键取消掉，这时一定要在代码中做好控制，
> 当数据加载完成后，必须要调用ProgressDialog的dismiss()方法来关闭对话框,
> 否则ProgressDialog将会一直存在。

## ListView
> 简单用法

```java
    private String data[] = {"Apple", "Banana", "Orange", "Watermelon", "Pear"};

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ArrayAdapter<String> adapter = new ArrayAdapter<String>(MainActivity.this, android.R.layout.simple_list_item_1, data);
        ListView listView = (ListView) findViewById(R.id.list_view);
        listView.setAdapter(adapter);
        listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {
                // 处理点击事件
            }
        });
    }
```

## RecyclerView
