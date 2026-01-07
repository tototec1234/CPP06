# C++ - Module 06

## C++キャスト

概要:
このドキュメントには、C++モジュールのModule 06の演習問題が含まれています。

バージョン: 8.0

---

# 第I章

## はじめに

**原文:**
```
C++ is a general-purpose programming language created by Bjarne Stroustrup as an extension of the C programming language, often referred to as "C with Classes" (source: Wikipedia).

The goal of these modules is to introduce you to Object-Oriented Programming. This will be the starting point of your C++ journey. Many languages are recommended for learning OOP, but we chose C++ since it is derived from your old friend, C. As C++ is a complex language, your code will adhere to the C++98 standard to keep things simple.

We acknowledge that modern C++ differs significantly in many aspects. If you want to become a proficient C++ developer, it will be up to you to explore further beyond the 42 Common Core!
```

**和訳:**
C++は、Bjarne StroustrupによってCプログラミング言語の拡張として作成された汎用プログラミング言語で、「C with Classes」（クラス付きC）と呼ばれることが多い（出典: Wikipedia）。

これらのモジュールの目標は、オブジェクト指向プログラミングを紹介することです。これはあなたのC++の旅の出発点となります。OOPを学ぶために多くの言語が推奨されていますが、私たちはC++を選択しました。それは、あなたの古い友達であるCから派生しているためです。C++は複雑な言語であるため、シンプルに保つために、あなたのコードはC++98標準に準拠します。

現代のC++は多くの側面で大きく異なることを認識しています。熟練したC++開発者になりたい場合は、42 Common Coreを超えてさらに探求するのはあなた次第です！

---

**注: 第II章（一般的なルール）と第IV章（AI指示）は、Module 05と同様の内容のため割愛しています。**

---

# 第III章

## 追加ルール

**原文:**
```
The following rule applies to the entire module and is mandatory.

For each exercise, type conversion must be handled using a specific type of casting. Your choice will be reviewed during the defense.
```

**和訳:**
以下のルールは、モジュール全体に適用され、必須です。

各演習では、型変換は特定のタイプのキャストを使用して処理する必要があります。あなたの選択は、防御中にレビューされます。

各演習では、型変換は特定のタイプのキャストを使用して処理する必要があります。あなたの選択は、防御中にレビューされます。

---

**注: 第IV章（AI指示）は、Module 05と同様の内容のため割愛しています。**

---

# 第V章

## 演習 00: スカラー型の変換

**原文:**
```
|  Exercise 00  |   |
| --- | --- |
|  Conversion of scalar types  |   |
|  Turn-in directory: ex00/  |   |
|  Files to turn in: Makefile, *.cpp, *.{h, hpp}  |   |
|  Allowed functions: Any function to convert from a string to an int, a float, or a double. This will help, but won't do the whole job.  |   |

Write a class ScalarConverter that will contain only one static method "convert" that will take as a parameter a string representation of a C++ literal in its most common form and output its value in the following series of scalar types:

- char
- int
- float
- double

As this class doesn't need to store anything at all, it must not be instantiable by users.

Except for char parameters, only the decimal notation will be used.

Examples of char literals: 'c', 'a', ...

To make things simple, please note that non-displayable characters shouldn't be used as inputs. If a conversion to char is not displayable, print an informative message.

Examples of int literals: 0, -42, 42...

Examples of float literals: 0.0f, -4.2f, 4.2f...

You have to handle these pseudo-literals as well (you know, for science): -inff, +inff, and nanf.

Examples of double literals: 0.0, -4.2, 4.2...
You have to handle these pseudo-literals as well (you know, for fun): -inf, +inf, and nan.

Write a program to test that your class works as expected.

You have to first detect the type of the literal passed as a parameter, convert it from string to its actual type, then convert it **explicitly** to the three other data types. Lastly, display the results as shown below.

If a conversion does not make any sense or overflows, display a message to inform the user that the type conversion is impossible. Include any header you need in order to handle numeric limits and special values.

|  ./convert 0  |
| --- |
|  char: Non displayable  |
|  int: 0  |
|  float: 0.0f  |
|  double: 0.0  |
|  ./convert nan  |
|  char: impossible  |
|  int: impossible  |
|  float: nanf  |
|  double: nan  |
|  ./convert 42.0f  |
|  char: '*'  |
|  int: 42  |
|  float: 42.0f  |
|  double: 42.0  |
```

**和訳:**
|  演習 00  |   |
| --- | --- |
|  スカラー型の変換  |   |
|  提出ディレクトリ: ex00/  |   |
|  提出ファイル: Makefile, *.cpp, *.{h, hpp}  |   |
|  許可された関数: 文字列をint、float、またはdoubleに変換する任意の関数。これは役立ちますが、すべての作業を行うわけではありません。  |   |

最も一般的な形式のC++リテラルの文字列表現をパラメータとして受け取り、次の一連のスカラー型でその値を出力する、静的メソッド「convert」を1つだけ含むScalarConverterクラスを作成してください：

- char
- int
- float
- double

このクラスは何も保存する必要がないため、ユーザーがインスタンス化できないようにする必要があります。

charパラメータを除いて、10進表記のみが使用されます。

charリテラルの例: 'c', 'a', ...

シンプルにするために、表示不可能な文字は入力として使用すべきではないことに注意してください。charへの変換が表示不可能な場合、情報メッセージを出力してください。

intリテラルの例: 0, -42, 42...

floatリテラルの例: 0.0f, -4.2f, 4.2f...

これらの疑似リテラルも処理する必要があります（科学のためです）: -inff, +inff, nanf。

doubleリテラルの例: 0.0, -4.2, 4.2...
これらの疑似リテラルも処理する必要があります（楽しみのためです）: -inf, +inf, nan。

クラスが期待どおりに機能することをテストするプログラムを作成してください。

まず、パラメータとして渡されたリテラルの型を検出し、文字列から実際の型に変換してから、**明示的に**他の3つのデータ型に変換する必要があります。最後に、以下に示すように結果を表示します。

変換が意味をなさないかオーバーフローする場合、型変換が不可能であることをユーザーに通知するメッセージを表示してください。数値の制限と特殊値を処理するために必要なヘッダーを含めてください。

|  ./convert 0  |
| --- |
|  char: Non displayable  |
|  int: 0  |
|  float: 0.0f  |
|  double: 0.0  |
|  ./convert nan  |
|  char: impossible  |
|  int: impossible  |
|  float: nanf  |
|  double: nan  |
|  ./convert 42.0f  |
|  char: '*'  |
|  int: 42  |
|  float: 42.0f  |
|  double: 42.0  |

---

# 第VI章

## 演習 01: シリアライゼーション

**原文:**
```
|  Exercise : 01  |   |
| --- | --- |
|  - Serialization  |   |
|  Turn-in directory: ex01/  |   |
|  Files to turn in: Makefile, *.cpp, *.{h, hpp}  |   |
|  Forbidden functions: None  |   |

Implement a class Serializer, which will not be initializable by the user in any way, with the following static methods:

uintptr_t serialize(Data* ptr);
It takes a pointer and converts it to the unsigned integer type uintptr_t.

Data* deserialization(uintptr_t raw);
It takes an unsigned integer parameter and converts it to a pointer to Data.

Write a program to test that your class works as expected.

You must create a non-empty (meaning it has data members) Data structure.

Use serialize() on the address of the Data object and pass its return value to deserialization(). Then, ensure the return value of deserialization() compares equal to the original pointer.

Do not forget to turn in the files of your Data structure.
```

**和訳:**
|  演習 : 01  |   |
| --- | --- |
|  - シリアライゼーション  |   |
|  提出ディレクトリ: ex01/  |   |
|  提出ファイル: Makefile, *.cpp, *.{h, hpp}  |   |
|  禁止された関数: なし  |   |

次の静的メソッドを持つ、ユーザーがどのような方法でも初期化できないSerializerクラスを実装してください：

uintptr_t serialize(Data* ptr);
ポインタを受け取り、符号なし整数型uintptr_tに変換します。

Data* deserialization(uintptr_t raw);
符号なし整数パラメータを受け取り、Dataへのポインタに変換します。

クラスが期待どおりに機能することをテストするプログラムを作成してください。

空でない（データメンバーを持つ）Data構造体を作成する必要があります。

Dataオブジェクトのアドレスでserialize()を使用し、その戻り値をdeserialization()に渡します。次に、deserialization()の戻り値が元のポインタと等しいことを確認してください。

Data構造体のファイルを提出することを忘れないでください。

---

# 第VII章

## 演習 02: 実際の型を識別する

**原文:**
```
|  Exercise:02  |   |
| --- | --- |
|  Identify real type  |   |
|  Turn-in directory: ex02/  |   |
|  Files to turn in: Makefile, *.cpp, *.{h, hpp}  |   |
|  Forbidden functions: std::typeinfo  |   |

Implement a Base class that has a public virtual destructor only. Create three empty classes A, B, and C, that publicly inherit from Base.

These four classes don't have to be designed in the Orthodox Canonical Form.

Implement the following functions:

Base * generate(void);
It randomly instantiates A, B, or C and returns the instance as a Base pointer. Feel free to use anything you like for the random choice implementation.

void identify(Base* p);
It prints the actual type of the object pointed to by p: "A", "B", or "C".

void identify(Base& p);
It prints the actual type of the object referenced by p: "A", "B", or "C". Using a pointer inside this function is forbidden.

Including the typeinfo header is forbidden.

Write a program to test that everything works as expected.
```

**和訳:**
|  演習:02  |   |
| --- | --- |
|  実際の型を識別する  |   |
|  提出ディレクトリ: ex02/  |   |
|  提出ファイル: Makefile, *.cpp, *.{h, hpp}  |   |
|  禁止された関数: std::typeinfo  |   |

パブリック仮想デストラクタのみを持つBaseクラスを実装してください。Baseから公開継承する3つの空のクラスA、B、Cを作成してください。

これら4つのクラスは、Orthodox Canonical Formで設計する必要はありません。

次の関数を実装してください：

Base * generate(void);
A、B、またはCをランダムにインスタンス化し、インスタンスをBaseポインタとして返します。ランダム選択の実装には、お好みのものを自由に使用してください。

void identify(Base* p);
pが指すオブジェクトの実際の型を出力します: "A", "B", または "C"。

void identify(Base& p);
pが参照するオブジェクトの実際の型を出力します: "A", "B", または "C"。この関数内でポインタを使用することは禁止されています。

typeinfoヘッダーを含めることは禁止されています。

すべてが期待どおりに機能することをテストするプログラムを作成してください。

---

**注: 第VIII章（提出とピア評価）は、Module 05と同様の内容のため割愛しています。**

