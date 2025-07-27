# Cff
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>حاسبة الأسعار - النسخة المحدثة</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary-color: #1a5d1a;
      --secondary-color: #2e7d32;
      --accent-color: #4caf50;
      --light-color: #e8f5e9;
      --dark-color: #1b5e20;
      --text-color: #222;
      --shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      font-family: 'Tahoma', 'Segoe UI', Arial, sans-serif;
      background: linear-gradient(135deg, #f4f4f4, #e0f2e9);
      color: var(--text-color);
      direction: rtl;
      text-align: right;
      padding: 20px;
      min-height: 100vh;
    }
    
    .container {
      max-width: 1000px;
      margin: 30px auto;
      background: #fff;
      padding: 30px;
      border-radius: 15px;
      box-shadow: var(--shadow);
      position: relative;
      overflow: hidden;
      border: 1px solid #ddd;
    }
    
    .container::before {
      content: "";
      position: absolute;
      top: 0;
      right: 0;
      width: 100%;
      height: 5px;
      background: linear-gradient(90deg, var(--accent-color), var(--secondary-color));
    }
    
    .header {
      text-align: center;
      margin-bottom: 25px;
      position: relative;
    }
    
    img.logo {
      max-width: 180px;
      display: block;
      margin: 0 auto 15px;
      filter: drop-shadow(0 2px 4px rgba(0,0,0,0.1));
    }
    
    h2 {
      color: var(--dark-color);
      font-size: 28px;
      margin-bottom: 5px;
      position: relative;
      display: inline-block;
      padding-bottom: 10px;
    }
    
    h2::after {
      content: "";
      position: absolute;
      bottom: 0;
      right: 0;
      width: 100px;
      height: 3px;
      background: var(--accent-color);
      border-radius: 3px;
    }
    
    .subtitle {
      color: #555;
      font-size: 16px;
      margin-top: 5px;
    }
    
    .form-container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      margin-bottom: 25px;
    }
    
    @media (max-width: 768px) {
      .form-container {
        grid-template-columns: 1fr;
      }
    }
    
    .form-group {
      margin-bottom: 18px;
      position: relative;
    }
    
    label {
      font-weight: bold;
      display: block;
      margin-bottom: 8px;
      color: var(--dark-color);
      font-size: 15px;
    }
    
    label i {
      margin-left: 5px;
      color: var(--accent-color);
    }
    
    input, select {
      width: 100%;
      padding: 12px 15px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 15px;
      transition: all 0.3s;
      background-color: #f9f9f9;
    }
    
    input:focus, select:focus {
      outline: none;
      border-color: var(--accent-color);
      box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
      background-color: #fff;
    }
    
    .dimensions-container {
      display: flex;
      gap: 15px;
    }
    
    .dimensions-container .form-group {
      flex: 1;
    }
    
    .button-group {
      display: flex;
      gap: 15px;
      margin-top: 25px;
      flex-wrap: wrap;
    }
    
    button {
      flex: 1;
      padding: 14px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-size: 16px;
      font-weight: bold;
      transition: all 0.3s;
      min-width: 120px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }
    
    @media (max-width: 480px) {
      .button-group {
        flex-direction: column;
      }
    }
    
    .calculate-btn {
      background: linear-gradient(to right, var(--secondary-color), var(--accent-color));
      color: white;
    }
    
    .reset-btn {
      background: linear-gradient(to right, #f44336, #e53935);
      color: white;
    }
    
    .save-btn {
      background: linear-gradient(to right, #2196f3, #1976d2);
      color: white;
    }
    
    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
    
    .calculate-btn:hover {
      background: linear-gradient(to right, var(--dark-color), var(--secondary-color));
    }
    
    .reset-btn:hover {
      background: linear-gradient(to right, #e53935, #c62828);
    }
    
    .save-btn:hover {
      background: linear-gradient(to right, #1976d2, #0d47a1);
    }
    
    .result-box {
      border: 1px dashed #aaa;
      padding: 25px;
      margin-top: 30px;
      background-color: #fafafa;
      border-radius: 10px;
      display: none;
    }
    
    .result-box h3 {
      color: var(--dark-color);
      margin-bottom: 15px;
      padding-bottom: 10px;
      border-bottom: 1px solid #eee;
      font-size: 22px;
    }
    
    .result-item {
      display: flex;
      justify-content: space-between;
      padding: 10px 0;
      border-bottom: 1px solid #eee;
    }
    
    .result-item:last-child {
      border-bottom: none;
    }
    
    .result-label {
      font-weight: bold;
      color: #555;
    }
    
    .result-value {
      font-weight: bold;
      color: var(--dark-color);
    }
    
    .summary {
      margin-top: 25px;
      font-size: 22px;
      font-weight: bold;
      color: var(--dark-color);
      text-align: center;
      padding: 20px;
      background: var(--light-color);
      border-radius: 10px;
      display: none;
    }
    
    .notes {
      display: flex;
      gap: 15px;
      margin-top: 25px;
      flex-wrap: wrap;
    }
    
    .note {
      flex: 1;
      min-width: 200px;
      padding: 15px;
      background: #f5f5f5;
      border-radius: 8px;
      font-size: 14px;
      color: #555;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    
    .note i {
      font-size: 20px;
      color: var(--accent-color);
    }
    
    .additional-option {
      background: #f0f7ff;
      padding: 15px;
      border-radius: 8px;
      margin-top: 15px;
      border-left: 4px solid #2196f3;
    }
    
    .progress-bar {
      height: 5px;
      background-color: #e0e0e0;
      border-radius: 5px;
      margin-bottom: 20px;
      overflow: hidden;
    }
    
    .progress {
      height: 100%;
      background: linear-gradient(to right, var(--accent-color), var(--secondary-color));
      width: 0%;
      transition: width 0.5s;
    }
    
    .footer {
      text-align: center;
      margin-top: 30px;
      color: #666;
      font-size: 14px;
      padding-top: 15px;
      border-top: 1px solid #eee;
    }
    
    .section-title {
      display: flex;
      align-items: center;
      gap: 10px;
      margin: 25px 0 15px;
      color: var(--dark-color);
      padding-bottom: 10px;
      border-bottom: 1px solid #eee;
    }
    
    .section-title i {
      color: var(--accent-color);
    }
    
    .required::after {
      content: " *";
      color: #f44336;
    }
    
    .checkbox-group {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-top: 10px;
    }
    
    .checkbox-group input {
      width: auto;
    }
    
    .specs-box {
      background: #f9f9f9;
      border-radius: 8px;
      padding: 15px;
      margin-top: 15px;
      border: 1px solid #e0e0e0;
      display: none;
    }
    
    .specs-box h4 {
      color: var(--dark-color);
      margin-bottom: 10px;
    }
    
    .spec-item {
      display: flex;
      justify-content: space-between;
      padding: 5px 0;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="progress-bar">
      <div class="progress" id="progress"></div>
    </div>
    
    <div class="header">
      <img src="https://i.imgur.com/ih5zjVj.png" class="logo" alt="شعار الشركة">
      <h2>حاسبة الأسعار المحدثة 🧮</h2>
      <p class="subtitle">أداة متكاملة لحساب أسعار النوافذ والأبواب وفق المواصفات الجديدة</p>
    </div>
    
    <div class="form-container">
      <div class="form-section">
        <div class="section-title">
          <i class="fas fa-cube"></i>
          <h3>تفاصيل المنتج</h3>
        </div>
        
        <div class="form-group">
          <label for="category" class="required">اختر القسم:</label>
          <select id="category">
            <option value="">-- اختر القسم --</option>
            <option value="نوافذ">نوافذ</option>
            <option value="أبواب">أبواب</option>
          </select>
        </div>
        
        <div class="form-group">
          <label for="type" class="required">اختر النوع:</label>
          <select id="type">
            <option value="">-- اختر القسم أولا --</option>
          </select>
        </div>
        
        <div class="form-group" id="subTypeContainer" style="display:none;">
          <label for="subType">تفاصيل إضافية:</label>
          <select id="subType">
            <option value="">-- اختر --</option>
          </select>
        </div>
        
        <div class="form-group" id="specsContainer" style="display:none;">
          <div class="specs-box" id="specsBox">
            <h4><i class="fas fa-info-circle"></i> المواصفات المحددة:</h4>
            <div class="spec-item">
              <span>نوع المنتج:</span>
              <span id="specType">--</span>
            </div>
            <div class="spec-item">
              <span>السعر الأساسي:</span>
              <span id="specPrice">--</span>
            </div>
            <div class="spec-item">
              <span>مقاس قياسي:</span>
              <span id="specStandard">--</span>
            </div>
            <div class="spec-item">
              <span>تكلفة الزيادة:</span>
              <span id="specExtra">--</span>
            </div>
          </div>
        </div>
        
        <div class="additional-option" id="curtainInput" style="display:none;">
          <label>مقاس الستارة (الطول × العرض):</label>
          <div class="dimensions-container">
            <div class="form-group">
              <input type="number" id="curtainLength" placeholder="الطول بالمتر" min="0.1" step="0.01">
            </div>
            <div class="form-group">
              <input type="number" id="curtainWidth" placeholder="العرض بالمتر" min="0.1" step="0.01">
            </div>
          </div>
        </div>
        
        <div class="form-group" id="ceilingCladdingContainer" style="display:none;">
          <label for="ceilingCladding">طول تلبيسة السقف (متر):</label>
          <input type="number" id="ceilingCladding" min="0" step="0.01" placeholder="طول التلبيسة بالمتر">
        </div>
      </div>
      
      <div class="form-section">
        <div class="section-title">
          <i class="fas fa-ruler-combined"></i>
          <h3>القياسات والكميات</h3>
        </div>
        
        <div class="additional-option" id="meshTypeContainer" style="display:none;">
          <div class="form-group">
            <label for="meshType">نوع الشبك:</label>
            <select id="meshType">
              <option value="">-- اختر نوع الشبك --</option>
              <option value="باب">باب (39 ريال/م²)</option>
              <option value="فولدنج">فولدنج (18 ريال/م²)</option>
              <option value="سلايد">سلايد (14 ريال/م²)</option>
            </select>
          </div>
        </div>
        
        <div class="dimensions-container">
          <div class="form-group">
            <label for="height" class="required">الطول (متر):</label>
            <input type="number" id="height" min="0.1" step="0.01" placeholder="مثال: 2.5">
          </div>
          
          <div class="form-group">
            <label for="width" class="required">العرض (متر):</label>
            <input type="number" id="width" min="0.1" step="0.01" placeholder="مثال: 1.8">
          </div>
        </div>
        
        <div class="form-group">
          <label for="quantity" class="required">الكمية:</label>
          <input type="number" id="quantity" value="1" min="1" max="100">
        </div>
        
        <div class="checkbox-group" id="curtainOption" style="display:none;">
          <input type="checkbox" id="addCurtain">
          <label for="addCurtain">إضافة ستارة داخلية (26 ريال/متر)</label>
        </div>
      </div>
    </div>
    
    <div class="button-group">
      <button class="calculate-btn" onclick="calculate()">
        <i class="fas fa-calculator"></i> احسب السعر
      </button>
      <button class="reset-btn" onclick="resetForm()">
        <i class="fas fa-redo"></i> إعادة تعيين
      </button>
      <button class="save-btn" onclick="saveAsWord()">
        <i class="fas fa-file-word"></i> حفظ كملف Word
      </button>
    </div>
    
    <div id="results" class="result-box">
      <h3><i class="fas fa-file-invoice"></i> تفاصيل الحساب</h3>
      <div class="result-item">
        <span class="result-label">سعر المنتج الأساسي:</span>
        <span class="result-value" id="basePrice">0 ريال</span>
      </div>
      <div class="result-item">
        <span class="result-label">تكلفة الستارة:</span>
        <span class="result-value" id="curtainCost">0 ريال</span>
      </div>
      <div class="result-item">
        <span class="result-label">تكلفة الشبك:</span>
        <span class="result-value" id="meshCost">0 ريال</span>
      </div>
      <div class="result-item">
        <span class="result-label">تكلفة الشحن:</span>
        <span class="result-value" id="shippingCost">0 ريال</span>
      </div>
      <div class="result-item">
        <span class="result-label">تكلفة تلبيسة السقف:</span>
        <span class="result-value" id="ceilingCost">0 ريال</span>
      </div>
      <div class="result-item">
        <span class="result-label">تكلفة الزيادة في المساحة:</span>
        <span class="result-value" id="extraAreaCost">0 ريال</span>
      </div>
      <div class="result-item" style="border-top: 2px solid #ccc; padding-top: 15px; margin-top: 5px;">
        <span class="result-label">المجموع قبل الضريبة:</span>
        <span class="result-value" id="subtotal">0 ريال</span>
      </div>
      <div class="result-item">
        <span class="result-label">الضريبة (15%):</span>
        <span class="result-value" id="tax">0 ريال</span>
      </div>
    </div>
    
    <div id="summary" class="summary">
      <i class="fas fa-receipt"></i> السعر النهائي: <span id="totalPrice">0</span> ريال
    </div>
    
    <div class="notes">
      <div class="note">
        <i class="fas fa-truck"></i>
        <span>الأسعار تشمل تكلفة الشحن</span>
      </div>
      <div class="note">
        <i class="fas fa-tools"></i>
        <span>الأسعار لا تشمل تكلفة التركيب</span>
      </div>
      <div class="note">
        <i class="fas fa-info-circle"></i>
        <span>الأسعار قابلة للتغيير حسب الكمية والمواصفات</span>
      </div>
    </div>
    
    <div class="footer">
      <p>© 2023 حاسبة الأسعار - جميع الحقوق محفوظة</p>
      <p>تم التحديث ليعكس الأسعار والمواصفات الجديدة</p>
    </div>
  </div>

  <script>
    // تعريف أسعار المنتجات وفقاً للمواصفات الجديدة
    const prices = {
      "نوافذ": {
        "دبل جلاس دبل فريم": {
          "ثابته": 34,
          "حركة": 73,
          "حركتين": 92,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "دبل جلاس سنجل فريم": {
          "ثابته": 26,
          "حركة": 46,
          "حركتين": 58,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "سنجل جلاس سنجل فريم": {
          "ثابته": 20,
          "حركة": 43,
          "حركتين": 47,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "نوافذ السلايدنج": {
          "price": 200,
          "standard": "لا يوجد",
          "extra": "+10 ريال لكل نافذة"
        },
        "نوافذ كهربائية": {
          "price": 102,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "سكاي لايت": {
          "بدون المكينه": 56,
          "مع المكينه": 145,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "كارتن وول": {
          "الثقيل": 56,
          "الأخف": 45,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "أبواب السحب": {
          "داخلي زجاج": 38,
          "داخلي متين": 41,
          "خارجي جزء مفتوح": 55,
          "خارجي جزئين مفتوحات": 58,
          "wpc سلايد": 61,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "حواجز الدرج": {
          "price": 43,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "حواجز الحمام": {
          "price": 32,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        }
      },
      "أبواب": {
        "باب المدخل": {
          "الزينك": 66,
          "ستينلس ستيل": 120,
          "الكاست المنيوم": 168,
          "standard": "لا يوجد",
          "extra": "+10 ريال لكل باب"
        },
        "أبواب WPC": {
          "فارغ": 45,
          "مع خشب": 50,
          "مع حشوة ضد الصوت": 60,
          "مع فريم ألمينيوم": 67,
          "سلايدنج wpc": 65,
          "standard": "2.2×1 متر",
          "extra": "كل 0.1م = 2 ريال"
        },
        "أبواب الألمنيوم": {
          "فارغ": 65,
          "مع خشب": 75,
          "فل المنيوم": 85,
          "الباب المخفي": 110,
          "باب المنيوم خارجي": 61,
          "standard": "2.2×1 متر",
          "extra": "كل 0.1م = 2 ريال"
        },
        "أبواب دورات المياه": {
          "النوع الجديد": 55,
          "النوع الاقدم": 45,
          "مخفي زجاجي": 65,
          "standard": "2.2×0.1 متر",
          "extra": "كل 0.1م = 2 ريال"
        },
        "أبواب السحب": {
          "داخلي زجاج": 38,
          "داخلي متين": 41,
          "خارجي جزء مفتوح": 55,
          "خارجي جزئين مفتوحات": 58,
          "wpc سلايد": 61,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "أبواب الفولدنج": {
          "داخلي": 39,
          "خارجي": 56,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "شتر دور خارجي": {
          "price": 28,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        },
        "أبواب الحدائق": {
          "price": 91,
          "standard": "لا يوجد",
          "extra": "لا يوجد"
        }
      }
    };
    
    // عناصر DOM
    const categorySelect = document.getElementById('category');
    const typeSelect = document.getElementById('type');
    const subTypeContainer = document.getElementById('subTypeContainer');
    const subTypeSelect = document.getElementById('subType');
    const specsContainer = document.getElementById('specsContainer');
    const specsBox = document.getElementById('specsBox');
    const curtainInput = document.getElementById('curtainInput');
    const curtainOption = document.getElementById('curtainOption');
    const meshTypeContainer = document.getElementById('meshTypeContainer');
    const meshTypeSelect = document.getElementById('meshType');
    const heightInput = document.getElementById('height');
    const widthInput = document.getElementById('width');
    const quantityInput = document.getElementById('quantity');
    const curtainLengthInput = document.getElementById('curtainLength');
    const curtainWidthInput = document.getElementById('curtainWidth');
    const ceilingCladdingContainer = document.getElementById('ceilingCladdingContainer');
    const ceilingCladdingInput = document.getElementById('ceilingCladding');
    const resultsDiv = document.getElementById('results');
    const summaryDiv = document.getElementById('summary');
    
    // تحديث شريط التقدم
    function updateProgress() {
      const progressBar = document.getElementById('progress');
      let progress = 0;
      
      if (categorySelect.value) progress += 20;
      if (typeSelect.value) progress += 20;
      if (heightInput.value && widthInput.value) progress += 40;
      if (quantityInput.value && quantityInput.value > 0) progress += 20;
      
      progressBar.style.width = progress + '%';
    }
    
    // تحديث أنواع المنتجات بناءً على القسم المختار
    categorySelect.addEventListener('change', function() {
      const category = this.value;
      typeSelect.innerHTML = '<option value="">-- اختر النوع --</option>';
      subTypeContainer.style.display = 'none';
      curtainInput.style.display = 'none';
      curtainOption.style.display = 'none';
      meshTypeContainer.style.display = 'none';
      ceilingCladdingContainer.style.display = 'none';
      specsContainer.style.display = 'none';
      
      if (category && prices[category]) {
        Object.keys(prices[category]).forEach(type => {
          const option = document.createElement('option');
          option.value = type;
          option.textContent = type;
          typeSelect.appendChild(option);
        });
      }
      
      updateProgress();
    });
    
    // تحديث الخيارات الإضافية بناءً على النوع المختار
    typeSelect.addEventListener('change', function() {
      const category = categorySelect.value;
      const type = this.value;
      
      subTypeContainer.style.display = 'none';
      curtainInput.style.display = 'none';
      curtainOption.style.display = 'none';
      meshTypeContainer.style.display = 'none';
      ceilingCladdingContainer.style.display = 'none';
      specsContainer.style.display = 'none';
      
      if (category && type) {
        const typeData = prices[category][type];
        
        // إظهار خيارات إضافية للأنواع التي لها تفاصيل
        if (typeof typeData === 'object' && 'price' in typeData === false) {
          subTypeContainer.style.display = 'block';
          subTypeSelect.innerHTML = '<option value="">-- اختر --</option>';
          
          Object.keys(typeData).forEach(key => {
            if (key !== 'standard' && key !== 'extra') {
              const option = document.createElement('option');
              option.value = key;
              option.textContent = key;
              subTypeSelect.appendChild(option);
            }
          });
        }
        
        // إظهار مواصفات المنتج
        if (typeData) {
          specsContainer.style.display = 'block';
          document.getElementById('specType').textContent = type;
          
          if ('price' in typeData) {
            document.getElementById('specPrice').textContent = typeData.price + ' ريال/م²';
          } else {
            document.getElementById('specPrice').textContent = 'يختلف حسب النوع';
          }
          
          document.getElementById('specStandard').textContent = typeData.standard || 'لا يوجد';
          document.getElementById('specExtra').textContent = typeData.extra || 'لا يوجد';
        }
        
        // إظهار خيارات الشبك للنوافذ من نوع الدبل جلاس
        if (category === 'نوافذ' && (type.includes('دبل جلاس') || type === 'سكاي لايت') {
          meshTypeContainer.style.display = 'block';
        }
        
        // إظهار خيار الستارة للنوافذ الدبل جلاس وأبواب السحب والفولدنج
        if ((category === 'نوافذ' && (type.includes('دبل جلاس') || type === 'نوافذ السلايدنج' || type === 'أبواب السحب')) || 
            (category === 'أبواب' && (type === 'أبواب السحب' || type === 'أبواب الفولدنج'))) {
          curtainOption.style.display = 'flex';
        }
        
        // إظهار خيار تلبيسة السقف لأبواب WPC
        if (category === 'أبواب' && type === 'أبواب WPC') {
          ceilingCladdingContainer.style.display = 'block';
        }
      }
      
      updateProgress();
    });
    
    // تحديث مواصفات المنتج عند تغيير النوع الفرعي
    subTypeSelect.addEventListener('change', function() {
      const category = categorySelect.value;
      const type = typeSelect.value;
      const subType = this.value;
      
      if (category && type && subType) {
        const typeData = prices[category][type];
        const subTypeData = typeData[subType];
        
        if (typeof subTypeData === 'object') {
          document.getElementById('specPrice').textContent = subTypeData.price + ' ريال/م²';
          document.getElementById('specStandard').textContent = subTypeData.standard || 'لا يوجد';
          document.getElementById('specExtra').textContent = subTypeData.extra || 'لا يوجد';
        } else {
          document.getElementById('specPrice').textContent = subTypeData + ' ريال/م²';
        }
      }
    });
    
    // تحديث شريط التقدم عند تغيير المدخلات
    [typeSelect, subTypeSelect, heightInput, widthInput, quantityInput].forEach(input => {
      input.addEventListener('input', updateProgress);
    });
    
    // حساب السعر وفقاً للمواصفات الجديدة
    function calculate() {
      // الحصول على القيم من المدخلات
      const category = categorySelect.value;
      const type = typeSelect.value;
      const subType = subTypeSelect.value;
      const height = parseFloat(heightInput.value) || 0;
      const width = parseFloat(widthInput.value) || 0;
      const quantity = parseInt(quantityInput.value) || 1;
      const curtainLength = parseFloat(curtainLengthInput.value) || 0;
      const curtainWidth = parseFloat(curtainWidthInput.value) || 0;
      const meshType = meshTypeSelect.value;
      const addCurtain = document.getElementById('addCurtain').checked;
      const ceilingCladding = parseFloat(ceilingCladdingInput.value) || 0;
      
      // التحقق من صحة المدخلات
      if (!category || !type || !height || !width) {
        alert('الرجاء ملء جميع الحقول المطلوبة');
        return;
      }
      
      // حساب المساحة الأساسية
      const area = height * width;
      
      // حساب سعر المنتج الأساسي
      let basePricePerUnit = 0;
      let basePrice = 0;
      let extraAreaCost = 0;
      let ceilingCost = 0;
      let shippingCost = 0;
      
      // الحصول على سعر الوحدة
      const typeData = prices[category][type];
      
      if (typeof typeData === 'object' && 'price' in typeData) {
        basePricePerUnit = typeData.price;
      } else if (typeof typeData === 'object' && subType && typeData[subType]) {
        if (typeof typeData[subType] === 'object') {
          basePricePerUnit = typeData[subType].price;
        } else {
          basePricePerUnit = typeData[subType];
        }
      } else if (typeof typeData === 'number') {
        basePricePerUnit = typeData;
      }
      
      // حساب السعر الأساسي وفقاً لنوع المنتج
      if (category === 'أبواب' && [
        'أبواب WPC', 
        'أبواب الألمنيوم', 
        'أبواب دورات المياه'
      ].includes(type)) {
        // حساب للمنتجات التي لها مقاس قياسي
        let standardArea = 0;
        if (type === 'أبواب دورات المياه') {
          standardArea = 2.2 * 0.1;
        } else {
          standardArea = 2.2 * 1;
        }
        
        const extraArea = Math.max(0, area - standardArea);
        const extraUnits = Math.ceil(extraArea / 0.1);
        extraAreaCost = extraUnits * 2 * quantity;
        
        basePrice = basePricePerUnit * quantity + extraAreaCost;
      } else if (type === 'نوافذ السلايدنج') {
        // نوافذ السلايدنج: (النوع * المساحة) + 10 ريال
        basePrice = (basePricePerUnit * area) + 10;
      } else {
        // المنتجات الأخرى: سعر المتر المربع
        basePrice = basePricePerUnit * area * quantity;
      }
      
      // إضافة 10 ريال لباب المدخل
      if (type === 'باب المدخل') {
        basePrice += 10 * quantity;
      }
      
      // حساب تكلفة تلبيسة السقف
      if (ceilingCladding > 0) {
        ceilingCost = Math.ceil(ceilingCladding) * 10 * quantity;
      }
      
      // حساب تكلفة الستارة
      let curtainCost = 0;
      if (addCurtain) {
        if (curtainLength > 0 && curtainWidth > 0) {
          // ستارة بقياسات محددة
          curtainCost = (curtainLength * curtainWidth) * 26 * quantity;
        } else {
          // ستارة داخلية (26 ريال للمتر)
          curtainCost = width * 26 * quantity;
        }
      }
      
      // حساب تكلفة الشبك
      const meshPrices = {
        "باب": 39,
        "فولدنج": 18,
        "سلايد": 14
      };
      const meshCost = meshType ? meshPrices[meshType] * area * quantity : 0;
      
      // حساب تكلفة الشحن
      if (type === 'كارتن وول') {
        shippingCost = 0.15 * area * quantity;
      } else if (type === 'باب المدخل') {
        shippingCost = area * 0.2 * quantity;
      } else if (type === 'أبواب WPC' || type === 'أبواب الألمنيوم') {
        const totalHeight = height + ceilingCladding;
        shippingCost = (totalHeight * width) * 0.11 * quantity;
      } else {
        shippingCost = basePrice * 0.05;
      }
      
      // المجموع الفرعي
      const subtotal = basePrice + curtainCost + meshCost + shippingCost + ceilingCost + extraAreaCost;
      
      // حساب الضريبة (15%)
      const tax = subtotal * 0.15;
      
      // السعر النهائي
      const total = subtotal + tax;
      
      // عرض النتائج
      document.getElementById('basePrice').textContent = basePrice.toFixed(2) + ' ريال';
      document.getElementById('curtainCost').textContent = curtainCost.toFixed(2) + ' ريال';
      document.getElementById('meshCost').textContent = meshCost.toFixed(2) + ' ريال';
      document.getElementById('shippingCost').textContent = shippingCost.toFixed(2) + ' ريال';
      document.getElementById('ceilingCost').textContent = ceilingCost.toFixed(2) + ' ريال';
      document.getElementById('extraAreaCost').textContent = extraAreaCost.toFixed(2) + ' ريال';
      document.getElementById('subtotal').textContent = subtotal.toFixed(2) + ' ريال';
      document.getElementById('tax').textContent = tax.toFixed(2) + ' ريال';
      document.getElementById('totalPrice').textContent = total.toFixed(2);
      
      resultsDiv.style.display = 'block';
      summaryDiv.style.display = 'block';
      
      // تمرير البيانات لحفظها
      window.calculationData = {
        category,
        type,
        subType,
        height,
        width,
        quantity,
        curtainLength,
        curtainWidth,
        meshType,
        basePrice,
        curtainCost,
        meshCost,
        shippingCost,
        ceilingCost,
        extraAreaCost,
        subtotal,
        tax,
        total
      };
    }
    
    // إعادة تعيين النموذج
    function resetForm() {
      categorySelect.value = '';
      typeSelect.innerHTML = '<option value="">-- اختر القسم أولا --</option>';
      subTypeContainer.style.display = 'none';
      curtainInput.style.display = 'none';
      curtainOption.style.display = 'none';
      meshTypeContainer.style.display = 'none';
      ceilingCladdingContainer.style.display = 'none';
      specsContainer.style.display = 'none';
      heightInput.value = '';
      widthInput.value = '';
      quantityInput.value = '1';
      curtainLengthInput.value = '';
      curtainWidthInput.value = '';
      ceilingCladdingInput.value = '';
      document.getElementById('addCurtain').checked = false;
      resultsDiv.style.display = 'none';
      summaryDiv.style.display = 'none';
      document.getElementById('progress').style.width = '0%';
    }
    
    // حفظ النتائج كملف Word
    function saveAsWord() {
      if (!window.calculationData) {
        alert('الرجاء إجراء الحساب أولاً');
        return;
      }
      
      const data = window.calculationData;
      
      // إنشاء محتوى HTML للوثيقة
      const content = `
        <!DOCTYPE html>
        <html>
        <head>
          <meta charset="UTF-8">
          <title>تفاصيل الحساب</title>
          <style>
            body { font-family: 'Tahoma', sans-serif; direction: rtl; text-align: right; padding: 20px; }
            h1 { color: #1b5e20; text-align: center; }
            table { width: 100%; border-collapse: collapse; margin: 20px 0; }
            th, td { padding: 10px; border: 1px solid #ddd; text-align: right; }
            th { background-color: #e8f5e9; }
            .total-row { font-weight: bold; background-color: #f1f8e9; }
            .section { margin-top: 30px; }
            .section-title { background-color: #1b5e20; color: white; padding: 10px; border-radius: 5px; }
          </style>
        </head>
        <body>
          <h1>تفاصيل الحساب</h1>
          
          <div class="section">
            <div class="section-title">معلومات المنتج</div>
            <table>
              <tr>
                <th>القسم</th>
                <td>${data.category}</td>
              </tr>
              <tr>
                <th>النوع</th>
                <td>${data.type}</td>
              </tr>
              ${data.subType ? `<tr>
                <th>التفاصيل</th>
                <td>${data.subType}</td>
              </tr>` : ''}
              <tr>
                <th>الطول</th>
                <td>${data.height} متر</td>
              </tr>
              <tr>
                <th>العرض</th>
                <td>${data.width} متر</td>
              </tr>
              <tr>
                <th>الكمية</th>
                <td>${data.quantity}</td>
              </tr>
              ${data.meshType ? `<tr>
                <th>نوع الشبك</th>
                <td>${data.meshType}</td>
              </tr>` : ''}
            </table>
          </div>
          
          <div class="section">
            <div class="section-title">تفاصيل الأسعار</div>
            <table>
              <tr>
                <th>البند</th>
                <th>القيمة (ريال)</th>
              </tr>
              <tr>
                <td>سعر المنتج الأساسي</td>
                <td>${data.basePrice.toFixed(2)}</td>
              </tr>
              ${data.curtainCost > 0 ? `<tr>
                <td>تكلفة الستارة</td>
                <td>${data.curtainCost.toFixed(2)}</td>
              </tr>` : ''}
              ${data.meshCost > 0 ? `<tr>
                <td>تكلفة الشبك</td>
                <td>${data.meshCost.toFixed(2)}</td>
              </tr>` : ''}
              ${data.ceilingCost > 0 ? `<tr>
                <td>تكلفة تلبيسة السقف</td>
                <td>${data.ceilingCost.toFixed(2)}</td>
              </tr>` : ''}
              ${data.extraAreaCost > 0 ? `<tr>
                <td>تكلفة الزيادة في المساحة</td>
                <td>${data.extraAreaCost.toFixed(2)}</td>
              </tr>` : ''}
              <tr>
                <td>تكلفة الشحن</td>
                <td>${data.shippingCost.toFixed(2)}</td>
              </tr>
              <tr class="total-row">
                <td>المجموع قبل الضريبة</td>
                <td>${data.subtotal.toFixed(2)}</td>
              </tr>
              <tr>
                <td>الضريبة (15%)</td>
                <td>${data.tax.toFixed(2)}</td>
              </tr>
              <tr class="total-row">
                <td>السعر النهائي</td>
                <td>${data.total.toFixed(2)}</td>
              </tr>
            </table>
          </div>
          
          <div class="section">
            <div class="section-title">ملاحظات</div>
            <ul>
              <li>الأسعار تشمل تكلفة الشحن</li>
              <li>الأسعار لا تشمل تكلفة التركيب</li>
              <li>الأسعار قابلة للتغيير حسب الكمية والمواصفات</li>
              <li>تم إنشاء هذا التقرير في ${new Date().toLocaleString('ar-EG')}</li>
            </ul>
          </div>
        </body>
        </html>
      `;
      
      // إنشاء ملف Blob
      const blob = new Blob([content], {type: 'application/msword'});
      
      // إنشاء رابط تنزيل
      const link = document.createElement('a');
      link.href = URL.createObjectURL(blob);
      link.download = `تفاصيل_الحساب_${new Date().toISOString().slice(0, 10)}.doc`;
      link.click();
    }
    
    // تهيئة شريط التقدم
    updateProgress();
  </script>
</body>
</html>
